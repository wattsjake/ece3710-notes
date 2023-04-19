**************
Space Invaders
**************
.. _space-invaders:

.. note::

   This project is under active development.

Introduction
############
.. _introduction:

Released in 1978 by Taito, Space invaders was one of the earliest “shooting”
video games. The goal is to defeat waves of alien invaders that zig-zag towards
Earth with a laser cannon, and of course, to score as many points as possible
doing it. The invaders have lasers too and they shoot them, more or less at
random, at the laser cannon and the shields that have been deployed for the
player’s defense. If the invaders reach Earth, the player loses. If the laser cannon
is destroyed (either by laser fire or by contact), the aliens regroup and attack the
next laser cannon. If all the aliens are destroyed, the player must face a new
wave of aliens that starts closer and moves faster.

    .. image:: images/space-invaders.png
        :width: 500
        :height: 350
        :alt: Space Invaders
        :align: center

Figure 1. Space InvadersTM

For this project, we use the LCD to display the laser cannon, the aliens and the
score. Shields are optional. One pushbutton is used to start the game and the
other is used to fire the laser cannon. The position of the laser cannon is
controlled by a potentiometer mounted near the display. Game parameters are
configured with a DIP switch.

Scope
#####
.. _scope:

This section specifies the scope of the document. The scope tells the reader what the
document covers, and more important, what it doesn't cover. 

Design Overview
###############
.. _design_overview:

Requirements
************
.. _requirements:

.. note::

   TODO: Fix the indentation of the requirements.

1. The system shall run on an external 9v DC supply.
2. The system shall use a 64x128 pixel LCD.
3. The system shall have a reset button, a start button and a fire button.
4. The system shall have a potentiometer located near the bottom of the LCD to
   control the position of the laser cannon.
5. The laser cannon shall be seven pixels high. The width shall be to 7, 9, 11 or 13
   pixels depending on the DIP switch.
6. Invaders shall be 6-8 pixels high. Those on the front row shall be 10 pixels wide
   with 3 pixels between them. Those on the back row may be narrower.
7. The system shall continually display a 4-digit score that tallies the number of
   aliens destroyed by the current player.
8. When the start button is pressed, the score shall be set to zero and an initial
   wave of alien attackers shall commence (see #9, below).
9. At the beginning of each wave, the display shall show (a) the laser cannon (at
   the bottom of the screen), and (b) 2 rows of 8 alien space invaders (arrayed on
   the left side of the screen). On the initial wave, the invaders shall be as far from
   the laser cannon as possible.
10. Once the battle begins, the formation of invaders shall move to the right, firing
   lasers at random. When the invaders reach the side of the display, they shall
   move 8 pixels closer to the laser cannon and reverse direction.
11. The invaders shall move left or right one pixel at a time. The movement speed of
   the invaders shall be roughly inversely proportional to the number of invaders on
   the screen.
12. The system must be able to display up to 8 simultaneous laser bursts (i.e.
   projectiles) from the invaders and up to 4 simultaneous laser bursts from the
   player's laser cannon. All laser bursts are one pixel in size and move at a
   uniform speed. To improve visibility, trailing pixels (up to 7) should be displayed.
13. If a laser burst hits an invader, the invader shall be destroyed. If all invaders are
   destroyed, a new wave begins with the aliens arrayed 8 pixels closer than before
   (but no more than 16 pixels total), and the battle continues with the movement
   speed of the aliens increased.
14. If a laser burst hits the laser cannon or if an invader reaches the bottom row (i.e.
   the row containing the laser cannon), the the game is over and the words GAME
   OVER shall appear until the start button is pressed.
15. A sound shall be generated each time the laser cannon fires, each time an
   invader is destroyed or when the game is over. The sound for each of these
   three events shall be different and (except for game over) shall not exceed 250
   milliseconds.
16. When the start button is pressed, the display may also show four equally spaced
   14x8 pixel shields. If a laser burst hits a shield, one pixel of that shield should be
   removed.
17. If the front row of space invaders ever overlaps the shields, the shields are
   removed.
18. At random times, a flying saucer may cross the screen behind the array of
   invaders. Hitting the saucer with a laser burst scores 50 points.
19. Use three or four rows of invaders instead of two.
20. Use two images for the invaders and alternate (animate) them each time the
   invaders move (See below).


Dependencies
************
.. _dependencies:

1. External 9v DC supply
2. 64x128 pixel LCD
3. Reset button, start button, fire button
4. Potentiometer to control the position of the laser cannon
5. Laser cannon with height of seven pixels and variable width of 7, 9, 11, or 13 pixels depending on the DIP switch
6. Invaders with a height of 6-8 pixels and width of 10 pixels for front row and narrower for back row
7. 4-digit score displayed continuously
8. Initial wave of alien attackers when start button is pressed
9. Display showing laser cannon and 2 rows of 8 alien space invaders on the left side of the screen at the beginning of each wave
10. Invader formation moves to the right, fires lasers randomly, and reverses direction when reaching the side of the display
11. Invaders move left or right one pixel at a time, with movement speed roughly inversely proportional to the number of invaders on the screen
12. Display up to 8 simultaneous laser bursts from the invaders and up to 4 simultaneous laser bursts from the player's laser cannon
13. New wave with aliens arrayed 8 pixels closer and increased movement speed when all invaders are destroyed
14. Game over if a laser burst hits the laser cannon or if an invader reaches the bottom row, with "GAME OVER" displayed until the start button is pressed
15. Sound generated for firing laser cannon, destroying an invader, or game over, with different sounds for each event and a maximum length of 250 milliseconds.

Theory of Operation
*******************
.. _theory_of_operation:

.. note::

   Add information about the theory of operation here.


Design Alternatives
*******************
.. _design_alternatives:

.. note::

   Add information about the design alternatives here.

Design Details
##############
.. _design_details:

This section addresses the design in detail, both what it is and why. Enough
information should be given so that someone with an engineering background could
implement the design. For example, timing analysis, schematics and code snippets
are an appropriate level of detail. Data sheets or software listings are not. That would
be too much detail. Still, expect over half of your document (not counting the
appendices) to be design details, so use subsections for clarity. 

Sprite Texture Generation
*************************
.. _sprite_texture_generation:

In Space Invaders, the sprite is a two-dimensional graphic representing the alien enemy characters that descend from the top of the screen. The sprite is made up of several pixels arranged in a specific pattern to create the appearance of an alien. There are two different types of sprites used in our game (shown below). As the aliens move across the screen, the sprite is animated to create the illusion of movement. The use of sprites in Space Invaders was an important aspect of the game's design, allowing for the creation of a large number of enemy characters on screen simultaneously while keeping the game running smoothly on the limited hardware of the time.

    .. image:: images/invaders-sprites.drawio.png
        :width: 650
        :height: 350
        :alt: Sprite 'UP' & 'DOWN'
        :align: center

Figure 2. Space Invaders Sprite 'UP' & 'DOWN'

In Space Invaders, the laser tank is a player-controlled sprite that moves horizontally across the bottom of the screen, firing a laser beam at the descending alien enemies. The size of the tank can be adjusted by changing the dip switches on the arcade game's circuit board, which can increase or decrease the tank's size by 7, 9, 11, or 13 pixels. This adjustment can significantly affect the gameplay experience, as a smaller tank can be more difficult to control but offers a smaller target for the enemy sprites, while a larger tank can be easier to maneuver but is also a larger target. The option to adjust the tank size via dip switches was a popular feature of the game among arcade operators and players, allowing for customization and variability in gameplay.

    .. image:: images/invaders-laser.drawio.png
        :width: 500
        :height: 350
        :alt: Sprite Laser Tank
        :align: center

Figure 3. Space Invaders Sprite Laser Tank

Timers and Interrupts
*********************************
.. _timers_and_interrupts:

The 8051 microcontroller has two 16-bit timers that can be used to generate delays, measure frequency, or create PWM signals. The microcontroller also has a watchdog timer to detect and recover from system faults. These timers are important features that provide precise timing and control in many applications.

Timer 0
-------
.. _timer_0:

Timer 0 is a 16-bit timer that is used to create delays in the Space Invaders game. The timer is configured using the following code found in the ``init.c`` file.

.. code-block:: c

   IE = 0x82; // Enable timer 0 interrupt
   TL0 = -18432 >> 8; // Load timer 0 low byte
   TH0 = -18432; // Load timer 0 high byte
   TR0 = 1; // Start timer 0

Timer 0 is used to trigger an interrupt every 10 milliseconds. Every time the timer 0 overflows it will trigger the following interrupt handler.

.. code-block:: c

   void interrupt_timer0(void)interrupt 1
   {
      TL0 = -18432 >> 8; //get high byte
      TH0 = -18432; //get low byte

      //if the timer is not zero, decrement it
      if(timer0 != 0)
      {
         timer0--;
      }
      else
      {
         timer0 = 100;
         timer0_flag = 1;
      }
   }

.. note::

   Add information about the timer 0 interrupt here.

Timer 2
-------
.. _timer_2:

Timer 2 is used for the ADC. The timer is configured using the following code found in the ``init.c`` file.

.. code-block:: c

   T2CON = 0x04;   // timer 2
   RCAP2H = -1844 >> 8; //get high byte
   RCAP2L = -1844; //get low byte

Everytime the timer 2 overflows it will trigger the following interrupt handler.

.. code-block:: c

   void interrupt_adc(void)interrupt 15
   {
      AD0INT = 0; //clear ADC0 interrupt flag
      adc_value = (ADC0H << 8) | ADC0L; //OR the two High and Low bits together
      sum += adc_value; //continually sum the pot
      count++; //add to count
      
      if(count >= 64)
      {
         avg = 0; //clear average
         avg = (sum >> 6);
         count = 0; //reset count
         sum = 0; //reset sum
         pot_flag = 1; //set pot flag}		
      }	
   }

.. note::

   Add information about the timer 2 interrupt here.

Timer



Sound Generation
****************
.. _sound_generation:

.. note::

   Add information about the sound generation here.


Hardware Schematic 
******************
.. _hardware_schematic:

.. note::

   Update the hardware schematic here.

Here is an image of the hardware schematic. Details need to be added.

    .. image:: images/project02-space-invaders-schematic.png
        :width: 500
        :height: 350
        :alt: 8051 Schematic
        :align: center


Testing
#######
.. _testing:

This section has two main purposes. First to describe the tests that are used to verify
the design meets the requirements, and second, to document the results of those
tests for your implementation. State for each test: (a) the test procedure, (b) the
observations to verify, (c) your observations, and (d) which requirements are
applicable. Be sure each requirement is covered by at least one test. 

Conclusion
##########
.. _conclusion:

This section summarizes test results makes observations about the performance and
functionality (or lack thereof) of the design. Also, not every design is optimal. It is
likely that you have acquired some insight along the way that will improve the design
for next time. This section is a good place to put that kind of information. 

Appendices
##########
.. _appendices:

This is the appropriate place to put items for reference only, such as software
listings. 







