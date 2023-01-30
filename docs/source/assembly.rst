Assembly Language Programming (8051)
==================================================

.. note:: This is a work in progress.  The information here is
          incomplete and may be inaccurate.  Please help by
          contributing to this document.

Introduction
------------

    "Do not pray for an easy life, pray for the strength to use the keyboard. - Bruce Lee"

The Assembly Language is a low level Language used to program microcongrollers and other devices. It's importatn to understand the hardware you are working with becuase that determines the way the assembly is coded. 


Jump, Loop, and Call Instructions
---------------------------------

The 8051 has a number of instructions that allow you to jump to a specific location in the program.  The most common of these are the jump instructions.  The jump instructions are:

    * JMP - unconditional jump
    * JZ - jump if zero
    * JNZ - jump if not zero
    * JC - jump if carry
    * JNC - jump if not carry
    * JB - jump if bit set
    * JNB - jump if bit not set
    * JBC - jump if bit set and clear bit
    * JNB - jump if bit not set and set bit

Example 1-1
-----------

Write a program that loads FFH into all of the registers.

.. code-block:: assembly

            MOV A, #FFH
            MOV R0, A
            MOV R1, A
            MOV R2, A
            MOV R3, A
            MOV R4, A
            MOV R5, A
            MOV R6, A
            MOV R7, A

----------------

Example 1-2
-----------

Write a program that links the switches to the LEDs.

.. code-block:: assembly

            MOV P1, #FFH
            MOV P2, #00H
    LOOP:   MOV A, P1
            MOV P2, A
            JMP LOOP

----------------

Example 3-3
-----------

Write a program to (a) load the accumulator witht he value 55H, (b) complement the ACC 700 times.

.. code-block:: assembly

            MOV A, #55H     ; load accumulator with 55H
            MOV R3, #10     ; load R3 with 10
    LOOP:   MOV R2, #70     ; load R2 with 70
    AGAIN:  CPL A           ; complement the accumulator
            DJNZ R2, AGAIN  ; decrement R2 and jump to AGAIN if not zero
            DJNZ R3, LOOP   ; decrement R3 and jump to LOOP if not zero

