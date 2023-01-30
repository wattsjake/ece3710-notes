************************************
Assembly Language Programming (8051)
************************************

.. note:: This is a work in progress. The information here is
          incomplete and may be inaccurate.  Please help by
          contributing to this document.

Introduction
************

.. note:: "**Do not pray for an easy life, pray for the strength to use the keyboard.** - *Bruce Lee*"

    .. image:: images/bruce-lee.jpg
        :width: 500
        :height: 350
        :alt: Bruce

The Assembly Language is a low level Language used to program microcongrollers and other devices. It's importatn to understand the hardware you are working with becuase that determines the way the assembly is coded. 

----------------

Jump, Loop, and Call Instructions
**********************************

The 8051 has a number of instructions that allow you to jump to a specific location in the program.  The most common of these are the jump instructions.  The jump instructions are:

    * **JMP**   - unconditional jump
    * **JZ**    - jump if zero
    * **JNZ**   - jump if not zero
    * **JC**    - jump if carry
    * **JNC**   - jump if not carry
    * **JB**    - jump if bit set
    * **JNB**   - jump if bit not set
    * **JBC**   - jump if bit set and clear bit
    * **JNB**   - jump if bit not set and set bit

The 8051 also has a number of instructions that allow you to loop through a section of code.  The most common of these are the loop instructions.  The loop instructions are:
    
        * **DJNZ**  - decrement and jump if not zero
        * **LJMP**  - long jump
        * **LCALL** - long call

The 8051 also has a number of instructions that allow you to call a subroutine.  The most common of these are the call instructions.  The call instructions are:
    
        * **CALL**  - call subroutine
        * **RET**   - return from subroutine
        * **RETI**  - return from interrupt

Example 1-1
-----------

Write a program that uses a jump, loop, and call instruction.

.. code-block:: assembly

            MOV A, #00H
            MOV R0, #10
    LOOP:   MOV A, #01H
            MOV R1, #10
    AGAIN:  MOV P1, A
            DJNZ R1, AGAIN
            DJNZ R0, LOOP
            CALL SUB
            RET
    SUB:    MOV P1, #FFH
            RET

----------------

Bit Manipulation Instructions
******************************

The 8051 has a number of instructions that allow you to manipulate bits.  The most common of these are the bit manipulation instructions.  The bit manipulation instructions are:

    * **CPL**   - complement bit
    * **CLR**   - clear bit
    * **SETB**  - set bit
    * **ANL**   - and bit
    * **ORL**   - or bit
    * **XRL**   - exclusive or bit

Example 1-2
-----------

Write a program that uses a bit manipulation instruction.

.. code-block:: assembly

            MOV A, #00H
            MOV R0, #10
    LOOP:   MOV A, #01H
            MOV R1, #10
    AGAIN:  MOV P1, A
            DJNZ R1, AGAIN
            DJNZ R0, LOOP
            CALL SUB
            RET
    SUB:    MOV P1, #FFH
            RET

----------------

Time Delay For Various 8051 Chips
*********************************

The 8051 has a delay instruction that allows you to delay for a specific amount of time.  The delay instruction is:

    * **NOP**   - no operation



