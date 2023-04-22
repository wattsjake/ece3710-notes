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
player's defense. If the invaders reach Earth, the player loses. If the laser cannon
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

Timer 4
-------
.. _timer_4:

Timer 4 is used for the ADC which generates the sound for the game. The timer is configured using the following code found in the ``init.c`` file.

.. code-block:: c

   DAC0CN = 0x94; //used for the DAC set to timer4 overflow left most 
   T4CON = 0x04;
   RCAP4H = 0;
   RCAP4L = 0; 

Everytime the timer 4 overflows it will trigger the following interrupt handler.

.. code-block:: c

   void interrupt_dac(void) interrupt 16
   {
      T4CON &= 0x7F; //clear the flag
      DAC0H = ((sine[phase] - 128) * envelope >> 10) + 128;
      if(phase<sizeof(sine)-1){phase++;}
      else if (duration>0){
         phase = 0;
         duration--;
         if(envelope>0){envelope--;}
         if(duration == 0){RCAP4H = RCAP4L = 0;} //reset timer4 H and L to zero
      }
   }

.. note::

   Add information about the timer 4 interrupt here.



Sound Generation
****************
.. _sound_generation:

Timer 4 is used to generate the sound for the game. Please see the section on timers and interrupts for more information about the timer 4 interrupt. The sound is generated using a sine wave. The following code is used for the sound generation. 'notes.h' is a header file that contains the frequencies for the notes.

.. note::

   Add quicklink to the section on timers and interrupts here.

.. code-block:: c

   #include <notes.h>
   //------------------- Sound Variables ------------------------
   unsigned long duration = 0;		// number of cycles left to output
   signed long envelope = 512;
   code unsigned char sine[] = { 176, 217, 244, 254, 244, 217, 176, 128, 80, 39, 12, 2, 12, 39, 80, 128 };
   unsigned char phase = sizeof(sine)-1;	// current point in sine to output

   /* 	---------- Play Notes ----------
	This function is used to play notes for the game.
   */
   void play_note(int note, int dur)
   {
      RCAP4H = -note >> 8;
      RCAP4L = -note;
      duration = (dur*1382L)/note;
      envelope = 512;
   }

The following code is an example of how the sound is generated for the game.

.. code-block:: c

   if(fire == 0 && counter == 25563){
      play_note(E5, 100);	
   }


Hardware Schematic 
******************
.. _hardware_schematic:

.. note::

   Update the hardware schematic here.

Here is an image of the hardware schematic. Details need to be added.

    .. image:: images/project02-space-invaders-schematic-rev1-1.png
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

Rest, Start, and Fire Buttons
-----------------------------
.. _rest_start_and_fire_buttons:

a. **Test Procedure:** Press the reset button, the start button, and the fire button. Check to see if the game resets, starts, and fires.

b. **Observations:** When the reset button was pressed the game returned to the 'start' menu. When the start button was pressed the game started. When the fire button was pressed the tank fired.

c. **Requirements:** The system shall have a reset button, a start button and a fire button.

Potentiometer
-------------
.. _potentiometer:

a. **Test Procedure:** Turn the potentiometer to the left and to the right. Check to see if the tank moves left and right.

b. **Observations:** When the potentiometer was turned to the left the tank moved left. When the potentiometer was turned to the right the tank moved right.

c. **Requirements:** The system shall have a potentiometer that controls the movement of the tank.



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

Include Files
*************
.. _include_files:

notes.h 
-------
.. _notes.h:

The following code is for reference to the note.h file.

.. code-block:: c

   #define C0 84550
   #define Cs0 79815
   #define Db0 79815
   #define D0 75335
   #define Ds0 71075
   #define Eb0 71075
   #define E0 67107
   #define F0 63326
   #define Fs0 59792
   #define Gb0 59792
   #define G0 56424
   #define Gs0 53251
   #define Ab0 53251
   #define A0 50269
   #define As0 47440
   #define Bb0 47440
   #define B0 44781
   #define C1 42275
   #define Cs1 39896
   #define Db1 39896
   #define D1 37657
   #define Ds1 35546
   #define Eb1 35546
   #define E1 33553
   #define F1 31670
   #define Fs1 29890
   #define Gb1 29890
   #define G1 28212
   #define Gs1 26631
   #define Ab1 26631
   #define A1 25135
   #define As1 23724
   #define Bb1 23724
   #define B1 22391
   #define C2 21134
   #define Cs2 19948
   #define Db2 19948
   #define D2 18829
   #define Ds2 17773
   #define Eb2 17773
   #define E2 16775
   #define F2 15833
   #define Fs2 14945
   #define Gb2 14945
   #define G2 14106
   #define Gs2 13314
   #define Ab2 13314
   #define A2 12567
   #define As2 11862
   #define Bb2 11862
   #define B2 11196
   #define C3 10568
   #define Cs3 9975
   #define Db3 9975
   #define D3 9415
   #define Ds3 8887
   #define Eb3 8887
   #define E3 8388
   #define F3 7917
   #define Fs3 7472
   #define Gb3 7472
   #define G3 7053
   #define Gs3 6657
   #define Ab3 6657
   #define A3 6284
   #define As3 5931
   #define Bb3 5931
   #define B3 5598
   #define C4 5284
   #define Cs4 4987
   #define Db4 4987
   #define D4 4707
   #define Ds4 4443
   #define Eb4 4443
   #define E4 4194
   #define F4 3958
   #define Fs4 3736
   #define Gb4 3736
   #define G4 3527
   #define Gs4 3329
   #define Ab4 3329
   #define A4 3142
   #define As4 2966
   #define Bb4 2966
   #define B4 2799
   #define C5 2642
   #define Cs5 2494
   #define Db5 2494
   #define D5 2354
   #define Ds5 2222
   #define Eb5 2222
   #define E5 2097
   #define F5 1979
   #define Fs5 1868
   #define Gb5 1868
   #define G5 1763
   #define Gs5 1664
   #define Ab5 1664
   #define A5 1571
   #define As5 1483
   #define Bb5 1483
   #define B5 1400
   #define C6 1321
   #define Cs6 1247
   #define Db6 1247
   #define D6 1177
   #define Ds6 1111
   #define Eb6 1111
   #define E6 1048
   #define F6 990
   #define Fs6 934
   #define Gb6 934
   #define G6 882
   #define Gs6 832
   #define Ab6 832
   #define A6 785
   #define As6 741
   #define Bb6 741
   #define B6 700
   #define C7 660
   #define Cs7 623
   #define Db7 623
   #define D7 588
   #define Ds7 555
   #define Eb7 555
   #define E7 524
   #define F7 495
   #define Fs7 467
   #define Gb7 467
   #define G7 441
   #define Gs7 416
   #define Ab7 416
   #define A7 393
   #define As7 371
   #define Bb7 371
   #define B7 350
   #define C8 330
   #define Cs8 312
   #define Db8 312
   #define D8 294
   #define Ds8 278
   #define Eb8 278

lcd.h 
-----
.. _lcd.h:

The following code is for reference to the lcd.h file.

.. code-block:: c

   //
   // LCD Interface
   //
   // This module initializes the 64x128 LCD module, declares a shadow memory
   // in external memory, and provides subroutines to blank the shadow memory
   // and/or copy that memory to the LCD.
   //
   //
   // initialize LCD - Call this once at the beginning of time.
   // It sets up LCD hardware, blanks the shadow memory then displays it on
   // the screen.
   //
   void init_lcd(void);

   //
   // Copy shadow memory to LCD screen.
   //
   void refresh_screen(void);

   //
   // Clear the shadow memory.
   //
   void blank_screen(void);

   //
   // Shadow memory. 1024 bytes. Eight 128-byte pages. Each page corresponds
   // to 8 rows of pixels. screen[0] is upper left, screen[127] is upper right,
   // screen[1023] is lower right. Least significant bit of each byte is on the
   // top pixel row of its page.
   //
   extern xdata char screen[];

   //
   // Handy 5x7 font that will come in handy in later labs. Always put at least
   // a one pixel space between characters.
   //
   extern code char font5x8[];

C8051F020_defs.h 
----------------
.. _C8051F020_defs.h:

The following code is for reference to the C8051F020_defs.h file.

.. code-block:: c

   //-----------------------------------------------------------------------------
   // C8051F020_defs.h
   //-----------------------------------------------------------------------------
   // Copyright 2007, Silicon Laboratories, Inc.
   // http://www.silabs.com
   //
   // Program Description:
   //
   // Register/bit definitions for the C8051F02x family.
   // **Important Note**: The si_toolchain.h header file should be included
   // before including this header file.
   //
   // Target:         C8051F020, 'F021, 'F022, 'F023
   // Tool chain:     Generic
   // Command Line:   None
   //
   // Release 1.4 - 20 AUG 2012 (TP)
   //    -Added #define for _XPAGE to provide support for SDCC memory paging
   //     (pdata)
   // Release 1.3 - 07 AUG 2007 (PKC)
   //    -Removed #include "si_toolchain.h". The C source file should include it.
   // Release 1.2 - 09 JUL 2007 (PKC)
   //    -Reformatted header file to enable portable SFR definitions

   //-----------------------------------------------------------------------------
   // Header File Preprocessor Directive
   //-----------------------------------------------------------------------------

   #ifndef C8051F020_DEFS_H
   #define C8051F020_DEFS_H

   //-----------------------------------------------------------------------------
   // Byte Registers
   //-----------------------------------------------------------------------------

   SI_SFR(P0, 0x80);                        // Port 0 Latch
   SI_SFR(SP, 0x81);                        // Stack Pointer
   SI_SFR(DPL, 0x82);                       // Data Pointer Low
   SI_SFR(DPH, 0x83);                       // Data Pointer High
   SI_SFR(P4, 0x84);                        // Port 4 Latch
   SI_SFR(P5, 0x85);                        // Port 5 Latch
   SI_SFR(P6, 0x86);                        // Port 6 Latch
   SI_SFR(PCON, 0x87);                      // Power Control
   SI_SFR(TCON, 0x88);                      // Timer/Counter Control
   SI_SFR(TMOD, 0x89);                      // Timer/Counter Mode
   SI_SFR(TL0, 0x8A);                       // Timer/Counter 0 Low
   SI_SFR(TL1, 0x8B);                       // Timer/Counter 1 Low
   SI_SFR(TH0, 0x8C);                       // Timer/Counter 0 High
   SI_SFR(TH1, 0x8D);                       // Timer/Counter 1 High
   SI_SFR(CKCON, 0x8E);                     // Clock Control
   SI_SFR(PSCTL, 0x8F);                     // Program Store R/W Control
   SI_SFR(P1, 0x90);                        // Port 1 Latch
   SI_SFR(TMR3CN, 0x91);                    // Timer/Counter 3 Control
   SI_SFR(TMR3RLL, 0x92);                   // Timer/Counter 3 Reload Low
   SI_SFR(TMR3RLH, 0x93);                   // Timer/Counter 3 Reload High
   SI_SFR(TMR3L, 0x94);                     // Timer/Counter 3 Low
   SI_SFR(TMR3H, 0x95);                     // Timer/Counter 3 High
   SI_SFR(P7, 0x96);                        // Port 7 Latch
   SI_SFR(SCON0, 0x98);                     // Serial Port UART0 Control
   SI_SFR(SBUF0, 0x99);                     // Serial Port UART0 Data Buffer
   SI_SFR(SPI0CFG, 0x9A);                   // SPI0 Configuration
   SI_SFR(SPI0DAT, 0x9B);                   // SPI0 Data
   SI_SFR(ADC1, 0x9C);                      // ADC1 Data
   SI_SFR(SPI0CKR, 0x9D);                   // SPI0 Clock Rate Control
   SI_SFR(CPT0CN, 0x9E);                    // Comparator 0 Control
   SI_SFR(CPT1CN, 0x9F);                    // Comparator 1 Control
   SI_SFR(P2, 0xA0);                        // Port 2 Latch
   SI_SFR(EMI0TC, 0xA1);                    // EMIF Timing Control
   SI_SFR(EMI0CF, 0xA3);                    // EMIF Configuration
   SI_SFR(P0MDOUT, 0xA4);                   // Port 0 Output Mode Configuration
   SI_SFR(P1MDOUT, 0xA5);                   // Port 1 Output Mode Configuration
   SI_SFR(P2MDOUT, 0xA6);                   // Port 2 Output Mode Configuration
   SI_SFR(P3MDOUT, 0xA7);                   // Port 3 Output Mode Configuration
   SI_SFR(IE, 0xA8);                        // Interrupt Enable
   SI_SFR(SADDR0, 0xA9);                    // Serial Port UART0 Slave Address
   SI_SFR(ADC1CN, 0xAA);                    // ADC1 Control
   SI_SFR(ADC1CF, 0xAB);                    // ADC1 Analog Mux Configuration
   SI_SFR(AMX1SL, 0xAC);                    // ADC1 Analog Mux Channel Select
   SI_SFR(P3IF, 0xAD);                      // Port 3 External Interrupt Flags
   SI_SFR(SADEN1, 0xAE);                    // Serial Port UART1 Slave Address Mask
   SI_SFR(EMI0CN, 0xAF);                    // EMIF Control
   SI_SFR(P3, 0xB0);                        // Port 3 Latch
   SI_SFR(OSCXCN, 0xB1);                    // External Oscillator Control
   SI_SFR(OSCICN, 0xB2);                    // Internal Oscillator Control
   SI_SFR(P74OUT, 0xB5);                    // Ports 4 - 7 Output Mode
   SI_SFR(FLSCL, 0xB6);                     // Flash Memory Timing Prescaler
   SI_SFR(FLACL, 0xB7);                     // Flash Acess Limit
   SI_SFR(IP, 0xB8);                        // Interrupt Priority
   SI_SFR(SADEN0, 0xB9);                    // Serial Port UART0 Slave Address Mask
   SI_SFR(AMX0CF, 0xBA);                    // ADC0 Mux Configuration
   SI_SFR(AMX0SL, 0xBB);                    // ADC0 Mux Channel Selection
   SI_SFR(ADC0CF, 0xBC);                    // ADC0 Configuration
   SI_SFR(P1MDIN, 0xBD);                    // Port 1 Input Mode
   SI_SFR(ADC0L, 0xBE);                     // ADC0 Data Low
   SI_SFR(ADC0H, 0xBF);                     // ADC0 Data High
   SI_SFR(SMB0CN, 0xC0);                    // SMBus0 Control
   SI_SFR(SMB0STA, 0xC1);                   // SMBus0 Status
   SI_SFR(SMB0DAT, 0xC2);                   // SMBus0 Data
   SI_SFR(SMB0ADR, 0xC3);                   // SMBus0 Slave Address
   SI_SFR(ADC0GTL, 0xC4);                   // ADC0 Greater-Than Register Low
   SI_SFR(ADC0GTH, 0xC5);                   // ADC0 Greater-Than Register High
   SI_SFR(ADC0LTL, 0xC6);                   // ADC0 Less-Than Register Low
   SI_SFR(ADC0LTH, 0xC7);                   // ADC0 Less-Than Register High
   SI_SFR(T2CON, 0xC8);                     // Timer/Counter 2 Control
   SI_SFR(T4CON, 0xC9);                     // Timer/Counter 4 Control
   SI_SFR(RCAP2L, 0xCA);                    // Timer/Counter 2 Capture Low
   SI_SFR(RCAP2H, 0xCB);                    // Timer/Counter 2 Capture High
   SI_SFR(TL2, 0xCC);                       // Timer/Counter 2 Low
   SI_SFR(TH2, 0xCD);                       // Timer/Counter 2 High
   SI_SFR(SMB0CR, 0xCF);                    // SMBus0 Clock Rate
   SI_SFR(PSW, 0xD0);                       // Program Status Word
   SI_SFR(REF0CN, 0xD1);                    // Voltage Reference 0 Control
   SI_SFR(DAC0L, 0xD2);                     // DAC0 Register Low
   SI_SFR(DAC0H, 0xD3);                     // DAC0 Register High
   SI_SFR(DAC0CN, 0xD4);                    // DAC0 Control
   SI_SFR(DAC1L, 0xD5);                     // DAC1 Register Low
   SI_SFR(DAC1H, 0xD6);                     // DAC1 Register High
   SI_SFR(DAC1CN, 0xD7);                    // DAC1 Control
   SI_SFR(PCA0CN, 0xD8);                    // PCA0 Control
   SI_SFR(PCA0MD, 0xD9);                    // PCA0 Mode
   SI_SFR(PCA0CPM0, 0xDA);                  // PCA0 Module 0 Mode Register
   SI_SFR(PCA0CPM1, 0xDB);                  // PCA0 Module 1 Mode Register
   SI_SFR(PCA0CPM2, 0xDC);                  // PCA0 Module 2 Mode Register
   SI_SFR(PCA0CPM3, 0xDD);                  // PCA0 Module 3 Mode Register
   SI_SFR(PCA0CPM4, 0xDE);                  // PCA0 Module 4 Mode Register
   SI_SFR(ACC, 0xE0);                       // Accumulator
   SI_SFR(XBR0, 0xE1);                      // Port I/O Crossbar Control 0
   SI_SFR(XBR1, 0xE2);                      // Port I/O Crossbar Control 1
   SI_SFR(XBR2, 0xE3);                      // Port I/O Crossbar Control 2
   SI_SFR(RCAP4L, 0xE4);                    // Timer 4 Capture Register Low
   SI_SFR(RCAP4H, 0xE5);                    // Timer 4 Capture Register High
   SI_SFR(EIE1, 0xE6);                      // External Interrupt Enable 1
   SI_SFR(EIE2, 0xE7);                      // External Interrupt Enable 2
   SI_SFR(ADC0CN, 0xE8);                    // ADC0 Control
   SI_SFR(PCA0L, 0xE9);                     // PCA0 Counter Low
   SI_SFR(PCA0CPL0, 0xEA);                  // PCA0 Capture 0 Low
   SI_SFR(PCA0CPL1, 0xEB);                  // PCA0 Capture 1 Low
   SI_SFR(PCA0CPL2, 0xEC);                  // PCA0 Capture 2 Low
   SI_SFR(PCA0CPL3, 0xED);                  // PCA0 Capture 3 Low
   SI_SFR(PCA0CPL4, 0xEE);                  // PCA0 Capture 4 Low
   SI_SFR(RSTSRC, 0xEF);                    // Reset Source Configuration/Status
   SI_SFR(B, 0xF0);                         // B Register
   SI_SFR(SCON1, 0xF1);                     // Serial Port UART1 Control
   SI_SFR(SBUF1, 0xF2);                     // Serail Port UART1 Data
   SI_SFR(SADDR1, 0xF3);                    // Serail Port UART1 Slave Address
   SI_SFR(TL4, 0xF4);                       // Timer/Counter 4 Low
   SI_SFR(TH4, 0xF5);                       // Timer/Counter 4 High
   SI_SFR(EIP1, 0xF6);                      // External Interrupt Priority 1
   SI_SFR(EIP2, 0xF7);                      // External Interrupt Priority 2
   SI_SFR(SPI0CN, 0xF8);                    // SPI0 Control
   SI_SFR(PCA0H, 0xF9);                     // PCA0 Counter High
   SI_SFR(PCA0CPH0, 0xFA);                  // PCA0 Capture 0 High
   SI_SFR(PCA0CPH1, 0xFB);                  // PCA0 Capture 1 High
   SI_SFR(PCA0CPH2, 0xFC);                  // PCA0 Capture 2 High
   SI_SFR(PCA0CPH3, 0xFD);                  // PCA0 Capture 3 High
   SI_SFR(PCA0CPH4, 0xFE);                  // PCA0 Capture 4 High
   SI_SFR(WDTCN, 0xFF);                     // Watchdog Timer Control

   //-----------------------------------------------------------------------------
   // 16-bit Register Definitions (might not be supported by all compilers)
   //-----------------------------------------------------------------------------

   SI_SFR16(DP, 0x82);                      // Data Pointer
   SI_SFR16(TMR3RL, 0x92);                  // Timer3 Reload Value
   SI_SFR16(TMR3, 0x94);                    // Timer3 Counter
   SI_SFR16(ADC0, 0xBE);                    // ADC0 Data
   SI_SFR16(ADC0GT, 0xC4);                  // ADC0 Greater Than Window
   SI_SFR16(ADC0LT, 0xC6);                  // ADC0 Less Than Window
   SI_SFR16(RCAP2, 0xCA);                   // Timer2 Capture/Reload
   SI_SFR16(T2, 0xCC);                      // Timer2 Counter
   SI_SFR16(TMR2RL, 0xCA);                  // Timer2 Capture/Reload
   SI_SFR16(TMR2, 0xCC);                    // Timer2 Counter
   SI_SFR16(RCAP4, 0xE4);                   // Timer4 Capture/Reload
   SI_SFR16(T4, 0xF4);                      // Timer4 Counter
   SI_SFR16(TMR4RL, 0xE4);                  // Timer4 Capture/Reload
   SI_SFR16(TMR4, 0xF4);                    // Timer4 Counter
   SI_SFR16(DAC0, 0xD2);                    // DAC0 Data
   SI_SFR16(DAC1, 0xD5);                    // DAC1 Data

   //-----------------------------------------------------------------------------
   // Address Definitions for bit-addressable SFRs
   //-----------------------------------------------------------------------------

   #define SFR_P0       0x80
   #define SFR_TCON     0x88
   #define SFR_P1       0x90
   #define SFR_SCON0    0x98
   #define SFR_P2       0xA0
   #define SFR_IE       0xA8
   #define SFR_P3       0xB0
   #define SFR_IP       0xB8
   #define SFR_SMB0CN   0xC0
   #define SFR_T2CON    0xC8
   #define SFR_PSW      0xD0
   #define SFR_PCA0CN   0xD8
   #define SFR_ACC      0xE0
   #define SFR_ADC0CN   0xE8
   #define SFR_B        0xF0
   #define SFR_SPI0CN   0xF8

   //-----------------------------------------------------------------------------
   // Bit Definitions
   //-----------------------------------------------------------------------------

   // TCON 0x88
   SI_SBIT(TF1, SFR_TCON, 7);               // Timer 1 Overflow Flag
   SI_SBIT(TR1, SFR_TCON, 6);               // Timer 1 On/Off Control
   SI_SBIT(TF0, SFR_TCON, 5);               // Timer 0 Overflow Flag
   SI_SBIT(TR0, SFR_TCON, 4);               // Timer 0 On/Off Control
   SI_SBIT(IE1, SFR_TCON, 3);               // Ext. Interrupt 1 Edge Flag
   SI_SBIT(IT1, SFR_TCON, 2);               // Ext. Interrupt 1 Type
   SI_SBIT(IE0, SFR_TCON, 1);               // Ext. Interrupt 0 Edge Flag
   SI_SBIT(IT0, SFR_TCON, 0);               // Ext. Interrupt 0 Type

   // SCON0 0x98
   SI_SBIT(SM00, SFR_SCON0, 7);             // Serial Mode Control Bit 0
   SI_SBIT(SM10, SFR_SCON0, 6);             // Serial Mode Control Bit 1
   SI_SBIT(SM20, SFR_SCON0, 5);             // Multiprocessor Communication Enable
   SI_SBIT(REN0, SFR_SCON0, 4);             // Receive Enable
   SI_SBIT(TB80, SFR_SCON0, 3);             // Transmit Bit 8
   SI_SBIT(RB80, SFR_SCON0, 2);             // Receive Bit 8
   SI_SBIT(TI0, SFR_SCON0, 1);              // Transmit Interrupt Flag
   SI_SBIT(RI0, SFR_SCON0, 0);              // Receive Interrupt Flag

   // IE 0xA8
   SI_SBIT(EA, SFR_IE, 7);                  // Global Interrupt Enable
   SI_SBIT(IEGF0, SFR_IE, 6);               // General Purpose Flag 0
   SI_SBIT(ET2, SFR_IE, 5);                 // Timer 2 Interrupt Enable
   SI_SBIT(ES0, SFR_IE, 4);                 // Uart0 Interrupt Enable
   SI_SBIT(ET1, SFR_IE, 3);                 // Timer 1 Interrupt Enable
   SI_SBIT(EX1, SFR_IE, 2);                 // External Interrupt 1 Enable
   SI_SBIT(ET0, SFR_IE, 1);                 // Timer 0 Interrupt Enable
   SI_SBIT(EX0, SFR_IE, 0);                 // External Interrupt 0 Enable

   // IP 0xB8
                                          // Bit7 UNUSED
                                          // Bit6 UNUSED
   SI_SBIT(PT2, SFR_IP, 5);                 // Timer 2 Priority
   SI_SBIT(PS, SFR_IP, 4);                  // Serial Port Priority
   SI_SBIT(PT1, SFR_IP, 3);                 // Timer 1 Priority
   SI_SBIT(PX1, SFR_IP, 2);                 // External Interrupt 1 Priority
   SI_SBIT(PT0, SFR_IP, 1);                 // Timer 0 Priority
   SI_SBIT(PX0, SFR_IP, 0);                 // External Interrupt 0 Priority

   // SMB0CN 0xC0
   SI_SBIT(BUSY, SFR_SMB0CN, 7);            // SMBus 0 Busy
   SI_SBIT(ENSMB, SFR_SMB0CN, 6);           // SMBus 0 Enable
   SI_SBIT(STA, SFR_SMB0CN, 5);             // SMBus 0 Start Flag
   SI_SBIT(STO, SFR_SMB0CN, 4);             // SMBus 0 Stop Flag
   SI_SBIT(SI, SFR_SMB0CN, 3);              // SMBus 0 Interrupt Pending Flag
   SI_SBIT(AA, SFR_SMB0CN, 2);              // SMBus 0 Assert/Acknowledge Flag
   SI_SBIT(SMBFTE, SFR_SMB0CN, 1);          // SMBus 0 Free Timer Enable
   SI_SBIT(SMBTOE, SFR_SMB0CN, 0);          // SMBus 0 Timeout Enable

   // T2CON 0xC8
   SI_SBIT(TF2, SFR_T2CON, 7);              // Timer 2 Overflow Flag
   SI_SBIT(EXF2, SFR_T2CON, 6);             // External Flag
   SI_SBIT(RCLK0, SFR_T2CON, 5);            // Uart0 Rx Clock Source
   SI_SBIT(TCLK0, SFR_T2CON, 4);            // Uart0 Tx Clock Source
   SI_SBIT(EXEN2, SFR_T2CON, 3);            // Timer 2 External Enable Flag
   SI_SBIT(TR2, SFR_T2CON, 2);              // Timer 2 On/Off Control
   SI_SBIT(CT2, SFR_T2CON, 1);              // Timer Or Counter Select
   SI_SBIT(CPRL2, SFR_T2CON, 0);            // Capture Or Reload Select

   //  PSW 0xD0
   SI_SBIT(CY, SFR_PSW, 7);                 // Carry Flag
   SI_SBIT(AC, SFR_PSW, 6);                 // Auxiliary Carry Flag
   SI_SBIT(F0, SFR_PSW, 5);                 // User Flag 0
   SI_SBIT(RS1, SFR_PSW, 4);                // Register Bank Select 1
   SI_SBIT(RS0, SFR_PSW, 3);                // Register Bank Select 0
   SI_SBIT(OV, SFR_PSW, 2);                 // Overflow Flag
   SI_SBIT(F1, SFR_PSW, 1);                 // User Flag 1
   SI_SBIT(P, SFR_PSW, 0);                  // Accumulator Parity Flag

   // PCA0CN 0xD8
   SI_SBIT(CF, SFR_PCA0CN, 7);              // PCA 0 Counter Overflow Flag
   SI_SBIT(CR, SFR_PCA0CN, 6);              // PCA 0 Counter Run Control Bit
                                          // Bit5 UNUSED
   SI_SBIT(CCF4, SFR_PCA0CN, 4);            // PCA 0 Module 4 Interrupt Flag
   SI_SBIT(CCF3, SFR_PCA0CN, 3);            // PCA 0 Module 3 Interrupt Flag
   SI_SBIT(CCF2, SFR_PCA0CN, 2);            // PCA 0 Module 2 Interrupt Flag
   SI_SBIT(CCF1, SFR_PCA0CN, 1);            // PCA 0 Module 1 Interrupt Flag
   SI_SBIT(CCF0, SFR_PCA0CN, 0);            // PCA 0 Module 0 Interrupt Flag

   // ADC0CN 0xE8
   SI_SBIT(AD0EN, SFR_ADC0CN, 7);           // ADC 0 Enable
   SI_SBIT(AD0TM, SFR_ADC0CN, 6);           // ADC 0 Track Mode
   SI_SBIT(AD0INT, SFR_ADC0CN, 5);          // ADC 0 Converision Complete Interrupt Flag
   SI_SBIT(AD0BUSY, SFR_ADC0CN, 4);         // ADC 0 Busy Flag
   SI_SBIT(AD0CM1, SFR_ADC0CN, 3);          // ADC 0 Start Of Conversion Mode Bit 1
   SI_SBIT(AD0CM0, SFR_ADC0CN, 2);          // ADC 0 Start Of Conversion Mode Bit 0
   SI_SBIT(AD0WINT, SFR_ADC0CN, 1);         // ADC 0 Window Compare Interrupt Flag
   SI_SBIT(AD0LJST, SFR_ADC0CN, 0);         // ADC 0 Right Justify Data Bit

   // SPI0CN 0xF8
   SI_SBIT(SPIF, SFR_SPI0CN, 7);            // SPI 0 Interrupt Flag
   SI_SBIT(WCOL, SFR_SPI0CN, 6);            // SPI 0 Write Collision Flag
   SI_SBIT(MODF, SFR_SPI0CN, 5);            // SPI 0 Mode Fault Flag
   SI_SBIT(RXOVRN, SFR_SPI0CN, 4);          // SPI 0 Rx Overrun Flag
   SI_SBIT(TXBSY, SFR_SPI0CN, 3);           // SPI 0 Tx Busy Flag
   SI_SBIT(SLVSEL, SFR_SPI0CN, 2);          // SPI 0 Slave Select
   SI_SBIT(MSTEN, SFR_SPI0CN, 1);           // SPI 0 Master Enable
   SI_SBIT(SPIEN, SFR_SPI0CN, 0);           // SPI 0 SPI Enable

   //-----------------------------------------------------------------------------
   // Interrupt Priorities
   //-----------------------------------------------------------------------------

   #define INTERRUPT_INT0           0     // External Interrupt 0
   #define INTERRUPT_TIMER0         1     // Timer0 Overflow
   #define INTERRUPT_INT1           2     // External Interrupt 1
   #define INTERRUPT_TIMER1         3     // Timer1 Overflow
   #define INTERRUPT_UART0          4     // Serial Port UART0
   #define INTERRUPT_TIMER2         5     // Timer2 Overflow
   #define INTERRUPT_SPI0           6     // SPI0 Interface
   #define INTERRUPT_SMBUS0         7     // SMBus0 Interface
   #define INTERRUPT_ADC0_WINDOW    8     // ADC0 Window Comparison
   #define INTERRUPT_PCA0           9     // PCA0 Peripheral
   #define INTERRUPT_COMPARATOR0F   10    // Comparator0 Falling Edge
   #define INTERRUPT_COMPARATOR0R   11    // Comparator0 Rising Edge
   #define INTERRUPT_COMPARATOR1F   12    // Comparator1 Falling Edge
   #define INTERRUPT_COMPARATOR1R   13    // Comparator1 Rising Edge
   #define INTERRUPT_TIMER3         14    // Timer3 Overflow
   #define INTERRUPT_ADC0_EOC       15    // ADC0 End Of Conversion
   #define INTERRUPT_TIMER4         16    // Timer4 Overflow
   #define INTERRUPT_ADC1_EOC       17    // ADC1 End Of Conversion
   #define INTERRUPT_INT6           18    // External Interrupt 6
   #define INTERRUPT_INT7           19    // External Interrupt 7
   #define INTERRUPT_UART1          20    // Serial Port UART1
   #define INTERRUPT_XTAL_READY     21    // External Crystal Oscillator Ready

   //-----------------------------------------------------------------------------
   // SDCC PDATA External Memory Paging Support
   //-----------------------------------------------------------------------------

   #if defined SDCC

   SI_SFR(_XPAGE, 0xAF); // Point to the EMI0CN register

   #endif

   //-----------------------------------------------------------------------------
   // Header File PreProcessor Directive
   //-----------------------------------------------------------------------------

   #endif                                 // #define C8051F020_DEFS_H

   //-----------------------------------------------------------------------------
   // End Of File
   //-----------------------------------------------------------------------------


.. note::

   Add include files here.







