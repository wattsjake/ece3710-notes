Appendix A
==========
.. _appendix_a:

Schematic
---------
.. _schematic:

    .. image:: images/project02-space-invaders-schematic-rev1-2.png
        :width: 600
        :height: 450
        :alt: 8051 Schematic
        :align: center

Space Invaders Schematic


Appendix B
==========
.. _appendix_b:

Include Files
-------------
.. _include_files:

notes.h 
^^^^^^^
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
^^^^^
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
^^^^^^^^^^^^^^^^
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
   // ^^Important Note^^: The si_toolchain.h header file should be included
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

debug.h 
^^^^^^^
.. _debug.h:

.. code-block:: c 

   #ifndef DEBUG_H 
   #define DEBUG_H

   extern unsigned char debug_line_pos;

   extern void debug_pot_position(unsigned char x);
   extern void debug_army_position(signed char x);
   extern void debug_draw_vertical_line(void);

   #endif

init.h 
^^^^^^
.. _init.h:

.. code-block:: c 

   #ifndef INIT_H 
   #define INIT_H

   extern long sum;
   extern unsigned int avg;

   extern void init(void);

   #endif

interrupt.h 
^^^^^^^^^^^
.. _interrupt.h:

.. code-block:: c 

   #ifndef INTERRUPTS_H 
   #define INTERRUPTS_H

   //----------------------ADC Variables-------------------------
   extern bit pot_flag;
   extern unsigned int adc_value; 
   extern unsigned int count; //used to determine when to update the adc value

   //------------------- Sound Variables ------------------------
   extern unsigned long duration;		// number of cycles left to output
   extern signed long envelope;
   extern code unsigned char sine[];
   extern unsigned char phase;	// current point in sine to output

   //----------------------Timer0 Variables------------------------
   extern unsigned int timer0;
   extern bit timer0_flag;

   #endif

invaders.h 
^^^^^^^^^^^
.. _invaders.h:

.. code-block:: c 

   #ifndef INVADERS_H 
   #define INVADERS_H
   //------------------------ Define ----------------------------
   #define MAX_LASER 10 //active lasers on the screen
   #define INVADERS_PAGE_START 1
   #define INVADERS_COL_START 15 //IMPORTANT: if you change this value you will need to adjust the invader_right_limit_array and invader_left_limit_array
   #define MAX_INVADERS 16
   #define LASER_ANIMATION_TIME_DELAY 2 //used to determine speed of laser
   #define INVADER_ANIMATION_TIME_DELAY 3 //used to determine speed of invader animation
   #define DEBOUNCE_BUTTON_TIME_DELAY 3// used for debounce stuff

   typedef struct{
      unsigned char active;
      unsigned long col;
      unsigned long page;
   } laser;

   typedef struct{
      unsigned char active;
      int col;
      int page;
   } invader_laser_list;
      
   extern xdata laser lasers[MAX_LASER];
   extern xdata invader_laser_list invader_lasers[MAX_LASER];
   // Fart deluxe variables (aka the bounding edges of the army)
   extern xdata unsigned long army_box_right;
   extern xdata unsigned long	army_box_left;
   extern int invaders_alive; 
   extern int army_page_offset;
   extern int army_col_offset; 
   extern int invader_left_dead;
   extern int invader_right_dead;
   extern int set_tank_pos;
   extern int player_lives; 
   extern int player_score;

   //master array that holds the state of each invader
   extern xdata unsigned char invader_array[16];
   #endif

Source Code
-----------
.. _source_code:


debug.c 
^^^^^^^
.. _debug.c:

.. code-block:: c 

   #include <C8051F020.h>
   #include <init.h>
   #include <lcd.h>
   #include <interrupts.h>

   unsigned char debug_line_pos;

   /** ----------- Debug Write Char ------------
   *  This funciton is used to write a character to the screen.
   */
   void debug_write_char(unsigned char page, unsigned char col, char ch)
   {
      int i = page * 128 + col;
      int j = (ch - ' ') * 5;
      unsigned char k;
      
      for(k=0; k<5;++k)
      {
         screen[i + k] = font5x8[j + k];    // OR operator paints in character rather than deleting pixels and refilling. Allows for smoother transistions?
      }
   }

   /* 	---------- Debug Pot Position ----------
   *	This function is used to debug the potentiometer. It will
   *	take the value of the pot and display it on the LCD. 
   */
   void debug_pot_position(unsigned char x)
   {
      debug_write_char(0,0, (x/100)%10 + 0x30);
      debug_write_char(0, 6, (x/10)%10 + 0x30);
      debug_write_char(0, 12, x%10 + 0x30);
   }

   /*  ---------- Debug Army Position ----------
   *    This function is used to debug the army position. It will
   *    take the value of the army and display it on the LCD.
   */
   void debug_army_position(signed char x)
   {
      //if x is negative, display a negative sign
      if(x < 0)
      {
         debug_write_char(0,20, '-');
         x = -x; //convert negative x to positive for correct display
      }
      debug_write_char(0,26, (x/100)%10 + 0x30);
      debug_write_char(0,32, (x/10)%10 + 0x30);
      debug_write_char(0,38, x%10 + 0x30);
   }

   /* ---------- Debug Draw Vertical Line ----------
   * Used for determining the actual column position of the screen
   */
   void debug_draw_vertical_line(void)
   {
      unsigned char i;
      if(pot_flag ==1)
      {
         pot_flag = 0; //reset flag
         debug_line_pos = ((avg * 128L) >> 12); //convert avg to be between 00-128
         debug_pot_position(debug_line_pos); //debug for pot	
         for(i=0; i<8; ++i)
         {
               screen[128 * i + debug_line_pos] = 0xFF; //draw vertical line
         }
         
      }

   }

init.c
^^^^^^
.. _init.c:

.. code-block:: c

   #include <C8051F020.h>
   #include <lcd.h>
   #include <init.h>

   long sum;
   unsigned int avg;

   void init(void)
   {
   //---------------- Initialization Code -------------------
      WDTCN = 0xde;   // disable watchdog
      WDTCN = 0xad;
      XBR2 = 0x40;    // enable port output

      OSCXCN = 0x67;            // turn on external crystal
      TMOD = 0x21;            // wait 1ms using T1 mode 2
      TH1 = -167;                // 2MHz clock, 167 counts - 1ms
      TR1 = 1;
      while(TF1 == 0){ }          // wait 1ms
      while(!(OSCXCN & 0x80)){ }  // wait till oscillator stable
      OSCICN = 8;                    // switch over to 22.1184MHz

      //--------------------- Registers ------------------------
      REF0CN = 0x03; // enable ADC
      ADC0CN = 0x8C; // ADC0 Control Register
      ADC0CF = 0x40; // ADC0 Configuration Register gain 1
      AMX0SL = 0x06; // AMUX0 Channel Select Register
      IE = 0x82;   // interupt enable
      EIE2 = 0x06; // Enable timer4 and ADC
      EIP2 = 0x04; // Highest Priority for timer4

      //---------------------- Timer 0 -------------------------
      /*
         Description of timer0 here. See function in invaders.c
      */
      TL0 = -18432 >> 8; //get high byte
      TH0 = -18432; //get low byte
      //turn on timer0
      TR0 = 1;
      
      //---------------------- Timer 2 -------------------------
      /*
         Used for the ADC
      */
      T2CON = 0x04;   // timer 2
      RCAP2H = -1844 >> 8; //get high byte
      RCAP2L = -1844; //get low byte

      //-------------- Initialization for ADC ------------------
      sum = 0;
      avg = 0;
      
      //---------------------- Timer 4 -------------------------
      /*
         Used for the DAC
      */
      DAC0CN = 0x94; //used for the DAC set to timer4 overflow left most 
      T4CON = 0x04;
      RCAP4H = 0;
      RCAP4L = 0; 

      CKCON = 0x60; // Remove divide by 12 for timer4 and timer2

      init_lcd(); // initialize the LCD screen
   }

interrupts.c
^^^^^^^^^^^^
.. _interrupts.c:

.. code-block:: c 

   #include <C8051F020.h>
   #include <init.h>

   #define TIMER0_VALUE 1

   //----------------------ADC Variables-------------------------
   bit pot_flag;
   unsigned int adc_value; 
   unsigned int count; //used to determine when to update the adc value

   //------------------- Sound Variables ------------------------
   unsigned long duration = 0;		// number of cycles left to output
   signed long envelope = 512;
   code unsigned char sine[] = { 176, 217, 244, 254, 244, 217, 176, 128, 80, 39, 12, 2, 12, 39, 80, 128 };
   unsigned char phase = sizeof(sine)-1;	// current point in sine to output

   //----------------------Timer0 Variables------------------------
   unsigned int timer0 = TIMER0_VALUE;
   bit timer0_flag;

   /*	---------- DAC Interrupt Serivce Routine ----------
      This function is used for the DAC which is used to play the 
      sounds.   
   */ 
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

   /*	---------- ADC Interrupt Serivce Routine ----------
      This function is used for the ADC. If the ADC0 interrupt flag
      is one (1) the program will be directed here. This service routine
      will happen roughly every 1 ms (If the clock is divide by 12). 
      An average is taken to avoid any noisey signal coming from the 
      pot on the dev board. This code we are taking 64 samples. Then 
      dividing by 64 by shifting right six (6). 
   */ 	
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

   /* ----------- Timer 0 Interrupt Service Routine --------
      Refer to page 117/272 in the data sheet for where the #1 comes from for timer0.
      timer0 overflows about every 10ms

      TODO: figure out how fast the timer 0 is running with an oscilloscope. Add
      information to READTHEDOCS
   */
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
         timer0 = TIMER0_VALUE;
         timer0_flag = 1;
      }
   }

invaders.c
^^^^^^^^^^
.. _invaders.c:

.. code-block:: c 

   
   #include <C8051F020.h>
   #include <lcd.h>
   #include <notes.h>
   #include <init.h>
   #include <interrupts.h>
   #include <debug.h>
   #include "invaders.h"
   #include "utils.h"

   //-------------------- BEGIN VARIABLES -----------------------

   //------------------- Global Game Variables ------------------
   int invaders_alive = 16;

   int army_page_offset = 0;
   int army_col_offset = 13;

   int player_score = 0;

   int set_tank_pos;

   int player_lives = 3;
   //------------------- Button Variables -----------------------
   sbit fire = P3^6;
   sbit start = P3^7;
   bit last_start = 0;
   bit last_fire = 0;

   //------------------- Laser Variables ------------------------
   unsigned char laser_time = LASER_ANIMATION_TIME_DELAY; //used to determine speed of laser
   unsigned int current_laser_pos = 0; 

   xdata unsigned char invader_array[16] = {1,1,1,1,1,1,1,1,
                                    1,1,1,1,1,1,1,1};
   xdata laser lasers[MAX_LASER];
   xdata invader_laser_list invader_lasers[MAX_LASER];

   // bounding edges of the army
   xdata unsigned long army_box_right = 100;
   xdata unsigned long army_box_left = 20;

   //--------------------- Invader Array ------------------------
   int army_dir_toggle = 0;
   int army_width = MAX_INVADERS/2;
   int invader_left_dead;
   int invader_right_dead;
   int not_dead = 1;

   unsigned char invader_animation_time = INVADER_ANIMATION_TIME_DELAY; //used to determine speed of invader animatio

   //------------------- Debounce Button ------------------------
   unsigned char debounce_time = DEBOUNCE_BUTTON_TIME_DELAY;


   //-------------------- END VARIABLES -------------------------

   //----------------------- Functions --------------------------

   /*
   * Funciton: Write a character to the screen
   * ----------------------------
   * Given a passed in character, write it to the screen
   * at the specified page and column
   * Arguments:
   *   unsigned char: page
   *   unsigned char: col
   *   char ch: character to write
   */
   void write_char(unsigned char page, unsigned char col, char ch)
   {
      int i = page * 128 + col;
      int j = (ch - ' ') * 5;
      unsigned char k;
      
      for(k=0; k<5;++k)
      {
         screen[i + k] = font5x8[j + k];    // OR operator paints in character rather than deleting pixels and refilling. Allows for smoother transistions?
      }
   }

   /*
   * Funciton: Write a string to the screen
   * ----------------------------
   * Given a passed in string, write it to the screen
   * at the specified page and column
   * Arguments:
   *   unsigned char: page
   *   unsigned char: col
   *   *char array: String to write
   */
   void write_string(unsigned char page, unsigned char col, char *temp)
   {
      while(*temp){
         write_char(page, col, *temp);
         temp++;
         col+=6;
      }
   }

   /*
   * Funciton: Write a specific byte to the screen
   * ----------------------------
   * Given a passed byte, write it to the screen
   * at the specified page and column
   * Arguments:
   *   unsigned char: page
   *   unsigned char: col
   *   unsigned char: val
   */
   void write_byte(unsigned char page, unsigned char col, unsigned char val)
   {
      if(col < 0 || col > 127){
         return;
      }
      screen[128 * page + col] = val;
   }

   /*
   * Funciton: Draw Sprite
   * ----------------------------
   * Given the desired sprite texture, (1 for up, 0 for down), 
   * write it to the screen.
   * at the specified page and column
   * Arguments:
   *   unsigned char: page
   *   unsigned char: col
   *   unsigned char: figure (desired sprite texture)
   */
   void draw_sprite(unsigned char page, unsigned char col, unsigned char figure)
   {
      static unsigned int code sprite_texture_tb[] = {
         0x70, 0x18, 0x7D, 0xB6, 0x3C, 0x3C, 0xB6, 0x7D, 0x18, 0x70, //first sprite
         0x0E, 0x98, 0x7D, 0x36, 0x3C, 0x3C, 0x36, 0x7D, 0x98, 0x0E};//second sprite
      unsigned char frame = figure * 10; //if figure is 0 then frame = 0, if figure is 1 then frame = 10

      unsigned char i = 0;
      for(i=0; i<10; i++)
      {
         write_byte(page, col+i, sprite_texture_tb[frame+i]);
      }
   }

   /*
   * Funciton: Add Cannon Laser
   * ----------------------------
   * When the player shoots a laser, add it to
   * the laser tracking array where the cannon is at
   * when the laser is shot.
   * Arguments:
   *   unsigned char: col
   * Global Variables:
   * 	laser lasers: array of lasers structs
   */
   void add_laser(int col)
   {
      int ii;
      for(ii = 0; ii < MAX_LASER; ii++){
         if(lasers[ii].active == 0){
            lasers[ii].active = 1;
            lasers[ii].page = 7;
            lasers[ii].col = col;
         }
      }
   }

   /*
   * Funciton: Update Cannon Lasers
   * ----------------------------
   * Iterates over the cannon laser array and updates
   * the laser position on the screen by decrementing
   * the laser page by 1.
   * Global Variables:
   * 	laser lasers: array of lasers structs
   */
   void update_lasers()
   {
      int ii;
      for(ii = 0; ii < MAX_LASER; ii++){
         if(lasers[ii].active == 1){
            screen[(lasers[ii].page * 128) + lasers[ii].col] = 0x00;
            lasers[ii].page--;
            screen[(lasers[ii].page * 128) + lasers[ii].col] = 0xFF;
            if(lasers[ii].page < 1){
               lasers[ii].active = 0;
            }
         }
      }
   }

   /*
   * Funciton: Draw Invader Army
   * ----------------------------
   * Given the offset for page and column, draw the invader army
   * using the invader array to determine which invaders are alive.
   * Arguments:
   *   unsigned char: page
   *   unsigned char: col
   *   unsigned char: figure (desired sprite texture)
   * Global Variables:
   * 	inavder array: array of invaders
   */
   void draw_army(unsigned char page, unsigned char col, unsigned char figure)
   {
      unsigned char i;
      unsigned char j;
      for(i = 0; i < 2; i++){
         for(j = 0; j < 8; j++){
            if(invader_array[i*8+j] == 1)//invader_array is a 16 element array
            {
               draw_sprite(page+i, col+j*13, figure);
            }
            else
            {
               continue; //if invader value is 0 then skip it
            }
         }
      }
   }

   /*
   * Funciton: Draw Cannon
   * ----------------------------
   * Draw the cannon at the position mapped to 
   * the potentiameter position
   * Arguments:
   *   unsigned char: x - Potentiometer position
   *   unsigned char: size - Width of cannon
   * Global Variables:
   * 	inavder array: array of invaders
   * Functions Called:
   * 	write_byte
   */
   void write_cannon(int x, unsigned char size)
   {
      int i = 0;
      write_byte(7, x, 0xFF);
      write_byte(7,x+1, 0xFE);
      write_byte(7,x-1, 0xFE);
      write_byte(7,x+2, 0xFC);
      write_byte(7,x-2, 0xFC);
      
      for(i = 0; i < size; i++){
         write_byte(7,x+3+i, 0xF8);
         write_byte(7,x-3-i, 0xF8);
      }
      for(i = size; i < 20; i++){
         write_byte(7,x+4+i, 0x00);
         write_byte(7,x-4-i, 0x00);
      }
   }

   /*
   * Funciton: Play Note
   * ----------------------------
   * Play a note for a given duration
   * Arguments:
   *   int note:  note to play
   *   int dur:  duration of note
   */
   void play_note(int note, int dur)
   {
      RCAP4H = -note >> 8;
      RCAP4L = -note;
      duration = (dur*1382L)/note;
      envelope = 512;
   }

   //---------------------- END FUNCTIONS -----------------------

   //----------------------- BEGIN MAIN -------------------------
   void main()
   {
      // Initilization for variables used in the main loop
      unsigned char ii;
      int margin;
      int padding_left;
      int padding_right;
      invader_left_dead = 0;
      invader_right_dead = 0;
      lasers[0].active = 0;
      lasers[1].active = 0;
      lasers[2].active = 0;
      invader_lasers[0].active = 0;
      invader_lasers[1].active = 0;
      invader_lasers[2].active = 0;
      
      //--------------------Initialize Code---------------------
      //use init.c to configure the initilization 
      //refer to init.c & init.h for more information
      init();

      // Set all 
      for(ii = 0; ii < MAX_LASER; ii++){
         lasers[ii].page = 0;
         lasers[ii].col = 0;
         lasers[ii].active = 0;
      }

      //--------------------- START SCREEN ---------------------
      while(start == 1)
      {
         write_string(1,46,"READY?");
         write_string(6,22,"PRESS START TO");
         write_string(7,49,"BEGIN");
         draw_army(3,13,0);
         refresh_screen();
         //debug_draw_vertical_line(); //draws vertical line TODO: fix so only single line
      }
      blank_screen(); //clear screen after start

      //--------------------- MAIN LOOP ---------------------
      while(not_dead)
      {		
         /**`
         * The follow if loops are for checking interrupts on timers
         * Flags:
         * 		pot_flag: 1 if potentiometer has changed
         * 		timer0_flag: 1 if timer0 has reached 0
         * 		laser_time: 1 if laser_time has reached 0
         * 		invader_animation_time: 1 if invader_animation_time has reached 0
         * 
         */
         if(pot_flag == 1) //If pot_flag == 1 update the position of the cannon
         {
            pot_flag = 0; //reset flag
            set_tank_pos = ((avg * 128L) >> 12); //convert avg to be between 00-128
            write_cannon(set_tank_pos, 3); //write cannon
            // debug_pot_position(set_tank_pos); //debug for pot
            refresh_screen();
         }
         if(timer0_flag == 1)
         {
            timer0_flag = 0;//reset flag from interrupts.c file
            laser_time--;
            invader_animation_time--;
            debounce_time--;
         }
         if(laser_time == 0)
         {
            laser_time = LASER_ANIMATION_TIME_DELAY; //reset laser_time
            update_lasers();
            collision_detect();
         }
         if(invader_animation_time == 0)
         {
            invader_animation_time = INVADER_ANIMATION_TIME_DELAY; //reset animation time
            blank_screen();
            update_lasers();
            draw_army(army_page_offset, army_col_offset, 0);
            
            army_width = invaders_alive / 2;
         


            if(invader_array[invader_left_dead] == 0){
               if(invader_array[invader_left_dead + 8] == 0){
                  invader_left_dead++;
               }
            }
            if(invader_array[7 - invader_right_dead] == 0){
               if(invader_array[7 - invader_right_dead + 8] == 0){
                  invader_right_dead++;
               }
            }			

            /**
            * The following code is for the movement of the army
            * and their direction
            */
            margin = 1;
            padding_right = (invader_right_dead * 13) + 13;
            padding_left = (invader_left_dead * 13) + 13;
            if(army_dir_toggle == 0){
               army_col_offset++;
               if(army_col_offset > padding_right + (13-margin)){
                  army_page_offset++;
                  army_dir_toggle = !army_dir_toggle;
               }
            }else{
               army_col_offset--;
               if(army_col_offset < margin - padding_left + 13){
                  army_page_offset++;
                  army_dir_toggle = !army_dir_toggle;
               }
            }

            collision_detect();
            debug_army_position((char)player_score);
            debug_pot_position((char)player_lives);
            
            update_invader_lasers();
            
            refresh_screen();
            P1^=1; //debug led light for animation
         }
         if(fire == 0){
            add_laser(set_tank_pos);
            //play_note(A4, 10);
            invader_laser();
         }
         if(player_lives <= 0){
            not_dead = 0;
         }
      }
      while(!not_dead){
         blank_screen();
         write_string(6,22,"DEAD");
         refresh_screen();
      }
      //--------------------- END MAIN LOOP ---------------------
   }
   //------------------------ END MAIN -------------------------

lcd.asm
^^^^^^^
.. _lcd.asm:

.. code-block:: assembly

   public init_lcd, refresh_screen, blank_screen, screen, font5x8;
   ?PR?lcd segment code
      rseg ?PR?lcd

   $include (c8051f020.inc)
   LCD_CMD   equ 8000h ; Set this to the address of the command register
   LCD_DAT   equ 8100h ; Set this to the address of the data register
   LCD_RESET equ 10h ; Mask that selects the reset line on P4 (e.g. for P4.4 use 10H)

   ;
   ; subroutines wcom and w_com_a
   ;   Writes a byte to the LCD command register after checking the busy flag first
   ;   Assumes the external memory interface is configured for split mode with bank
   ;   select.
   ; inputs:
   ;   wcom:   r0  = byte to write to command register
   ;   wcom_a: acc = byte to write to command register
   ; outputs: none
   ; destroys:
   ;   wcom:   EMI0CN
   ;   wcom_a: EMI0CN, r0
   wcom_a:	mov	r0,a		; save acc in R0 while we check BUSY
   wcom:	mov	EMI0CN,#HIGH LCD_CMD ; command/status register
   wcom1:	movx	a,@r0		; r0 has no relevance here
      jb	acc.7,wcom1	; wait for not BUSY
      mov	a,r0		; get the actual data to write
      movx	@r0,a		; write the command, r0 is irrelevant here
      ret
   ;
   ; subroutines wdat and w_dat_a and w_datc
   ;   Writes a byte to the LCD data register after checking the busy flag first
   ;   Assumes the external memory interface is configured for split mode with bank
   ;   select.
   ; inputs:
   ;   wdat:   r0  = byte to write to data register
   ;   wdat_a: acc = byte to write to data register
   ;   wdat_c: acc = dptr-relative index (dptr[acc]) of byte to write to data register 
   ; outputs: none
   ; destroys:
   ;   wdat:   EMI0CN
   ;   wdat_a: EMI0CN, r0
   ;   wdat_c: EMI0CN, r0
   wdat_c:	movc	a,@a+dptr	; lookup byte to write (handy for fonts)
   wdat_a:	mov	r0,a		; save it in R0 while we check BUSY
   wdat:	mov	EMI0CN,#HIGH LCD_CMD ; command/status register
   wdat1:	movx	a,@r0		; r0 has no relevance here
      jb	acc.7,wdat1	; wait for not BUSY
      mov	EMI0CN,#HIGH LCD_DAT	; data register
      mov	a,r0		; actual data to write
      movx	@r0,a		; write the data, r0 is irrelevant here
      ret
   ;
   ; Initialize controller for S64128N LCD module
   ;   inputs: none
   ;   outputs: none
   ;   destroys: r0, r2, r3, dptr
   ;
   init_lcd:
      mov	p4,#not LCD_RESET
      mov	emi0cf,#28h     ; B5: P4-7, B4: multiplexed, B3-2: split bank
      mov	emi0tc,#4Dh     ; pulse width 4 sysclock cycles
      mov	p74out,#0FFH    ; push-pull
      orl p4,#LCD_RESET   ; assert then deassert reset

      mov	R0,#02FH	; Boost on, voltage Reg and follower on
      call	wcom
      mov	R0,#0A2H;	; 1/9bias selected
      call	wcom
      mov	R0,#0A1H	; reverse segment driver output seg131-seg0
      call	wcom
      mov 	R0,#0C0H	; common output mode com0 to com63
      call 	wcom
      mov 	R0,#024H	; Ra/Rb ratio
      call 	wcom
      mov 	R0,#081H	; electronic vloume mode set
      call 	wcom
      mov 	R0,#026H	; contrast
      call 	wcom
      mov 	R0,#040H	; display line address = 0
      call 	wcom
      mov 	R0,#0A6H	; normal video
      call 	wcom
      mov 	R0,#0AFH	; display on
      call 	wcom
      call	blank_screen	; fall through to refresh_screen
   ;
   ; subroutine refresh_screen
   ;   Copies 1k bytes of data from external address 0 to the LCD. Bytes 0-7F go
   ;   into page 0, bytes 80-FF go to page 1 etc.
   ; inputs: none
   ; outputs: none
   ; destroys: r0, r2, r3, dptr, EMI0CN
   ;
   refresh_screen:
      mov	dptr,#0		; start of 1k block of memory
      mov	r2,#0B0H	; command to set page number to 0
   page_loop:
      mov	a,r2		; set page number n, n = 0, 1, 2...7
      call	wcom_a
      mov	a,#04H		; set column number to 4. If LCD is not
      call	wcom_a		; inverted, you will want to set column
      mov	a,#10H		; number to 0.
      call	wcom_a
      mov	r3,#128		; copy 128 bytes
   byte_loop:
      movx	a,@dptr		; get byte from memory
      call	wdat_a		; and write it to the LCD
      inc	dptr
      djnz	r3,byte_loop
      inc	r2		; advance to next page, but bail if it is 8 (B8)
      cjne	r2,#0B8H,page_loop
      ret

   blank_screen:
      mov	dptr,#0
      mov	a,#00h
      
   blank_loop:
      movx @dptr,a
      inc	dptr
      mov	b,dph
      jnb	b.2,blank_loop
      ret

   font5x8:
   db  000H, 000H, 000H, 000H, 000H ;  
   db  000H, 006H, 05FH, 006H, 000H ; !
   db  007H, 003H, 000H, 007H, 003H ; "
   db  024H, 07EH, 024H, 07EH, 024H ; #
   db  024H, 02BH, 06AH, 012H, 000H ; $
   db  063H, 013H, 008H, 064H, 063H ; %
   db  036H, 049H, 056H, 020H, 050H ; &
   db  000H, 007H, 003H, 000H, 000H ; '
   db  000H, 03EH, 041H, 000H, 000H ; (
   db  000H, 041H, 03EH, 000H, 000H ; )
   db  008H, 03EH, 01CH, 03EH, 008H ; *
   db  008H, 008H, 03EH, 008H, 008H ; +
   db  000H, 0E0H, 060H, 000H, 000H ; ,
   db  008H, 008H, 008H, 008H, 008H ; -
   db  000H, 060H, 060H, 000H, 000H ; .
   db  020H, 010H, 008H, 004H, 002H ; /
   db  03EH, 051H, 049H, 045H, 03EH ; 0
   db  000H, 042H, 07FH, 040H, 000H ; 1
   db  062H, 051H, 049H, 049H, 046H ; 2
   db  022H, 049H, 049H, 049H, 036H ; 3
   db  018H, 014H, 012H, 07FH, 010H ; 4
   db  02FH, 049H, 049H, 049H, 031H ; 5
   db  03CH, 04AH, 049H, 049H, 030H ; 6
   db  001H, 071H, 009H, 005H, 003H ; 7
   db  036H, 049H, 049H, 049H, 036H ; 8
   db  006H, 049H, 049H, 029H, 01EH ; 9
   db  000H, 06CH, 06CH, 000H, 000H ; :
   db  000H, 0ECH, 06CH, 000H, 000H ; ;
   db  008H, 014H, 022H, 041H, 000H ; <
   db  024H, 024H, 024H, 024H, 024H ; =
   db  000H, 041H, 022H, 014H, 008H ; >
   db  002H, 001H, 059H, 009H, 006H ; ?
   db  03EH, 041H, 05DH, 055H, 01EH ; @
   db  07EH, 011H, 011H, 011H, 07EH ; A
   db  07FH, 049H, 049H, 049H, 036H ; B
   db  03EH, 041H, 041H, 041H, 022H ; C
   db  07FH, 041H, 041H, 041H, 03EH ; D
   db  07FH, 049H, 049H, 049H, 041H ; E
   db  07FH, 009H, 009H, 009H, 001H ; F
   db  03EH, 041H, 049H, 049H, 07AH ; G
   db  07FH, 008H, 008H, 008H, 07FH ; H
   db  000H, 041H, 07FH, 041H, 000H ; I
   db  030H, 040H, 040H, 040H, 03FH ; J
   db  07FH, 008H, 014H, 022H, 041H ; K
   db  07FH, 040H, 040H, 040H, 040H ; L
   db  07FH, 002H, 004H, 002H, 07FH ; M
   db  07FH, 002H, 004H, 008H, 07FH ; N
   db  03EH, 041H, 041H, 041H, 03EH ; O
   db  07FH, 009H, 009H, 009H, 006H ; P
   db  03EH, 041H, 051H, 021H, 05EH ; Q
   db  07FH, 009H, 009H, 019H, 066H ; R
   db  026H, 049H, 049H, 049H, 032H ; S
   db  001H, 001H, 07FH, 001H, 001H ; T
   db  03FH, 040H, 040H, 040H, 03FH ; U
   db  01FH, 020H, 040H, 020H, 01FH ; V
   db  03FH, 040H, 03CH, 040H, 03FH ; W
   db  063H, 014H, 008H, 014H, 063H ; X
   db  007H, 008H, 070H, 008H, 007H ; Y
   db  071H, 049H, 045H, 043H, 000H ; Z
   db  000H, 07FH, 041H, 041H, 000H ; [
   db  002H, 004H, 008H, 010H, 020H ; \
   db  000H, 041H, 041H, 07FH, 000H ; ]
   db  004H, 002H, 001H, 002H, 004H ; ^
   db  080H, 080H, 080H, 080H, 080H ; _
   db  000H, 003H, 007H, 000H, 000H ; `
   db  020H, 054H, 054H, 054H, 078H ; a
   db  07FH, 044H, 044H, 044H, 038H ; b
   db  038H, 044H, 044H, 044H, 028H ; c
   db  038H, 044H, 044H, 044H, 07FH ; d
   db  038H, 054H, 054H, 054H, 008H ; e
   db  008H, 07EH, 009H, 009H, 000H ; f
   db  018H, 0A4H, 0A4H, 0A4H, 07CH ; g
   db  07FH, 004H, 004H, 078H, 000H ; h
   db  000H, 000H, 07DH, 040H, 000H ; i
   db  040H, 080H, 084H, 07DH, 000H ; j
   db  07FH, 010H, 028H, 044H, 000H ; k
   db  000H, 000H, 07FH, 040H, 000H ; l
   db  07CH, 004H, 018H, 004H, 078H ; m
   db  07CH, 004H, 004H, 078H, 000H ; n
   db  038H, 044H, 044H, 044H, 038H ; o
   db  0FCH, 044H, 044H, 044H, 038H ; p
   db  038H, 044H, 044H, 044H, 0FCH ; q
   db  044H, 078H, 044H, 004H, 008H ; r
   db  008H, 054H, 054H, 054H, 020H ; s
   db  004H, 03EH, 044H, 024H, 000H ; t
   db  03CH, 040H, 020H, 07CH, 000H ; u
   db  01CH, 020H, 040H, 020H, 01CH ; v
   db  03CH, 060H, 030H, 060H, 03CH ; w
   db  06CH, 010H, 010H, 06CH, 000H ; x
   db  09CH, 0A0H, 060H, 03CH, 000H ; y
   db  064H, 054H, 054H, 04CH, 000H ; z
   db  008H, 03EH, 041H, 041H, 000H ; {
   db  000H, 000H, 077H, 000H, 000H ; |
   db  000H, 041H, 041H, 03EH, 008H ; }
   db  002H, 001H, 002H, 001H, 000H ; ~
   db  006H, 009H, 009H, 006H, 000H ; ?

      xseg
   screen:	ds 1024

      end


utils.c 
^^^^^^^
.. _utils.c

.. code-block:: c 

   
   #include <C8051F020.h>
   #include <init.h>
   #include <lcd.h>
   #include <interrupts.h>
   #include "invaders.h"


   /*
   * Function: Detect a collision between a laser and the tank
   * ---------------------------- 
   * Globals:
   *   unsigned int: left boundry of army block
   *   unsigned int: right boundry of army block
   *   unsigned char array: army block    
   *   laser lasers: array of lasers
   */
   void collision_tank_detect(){
      int ii;
      int col_temp;
      int page_temp;

      for(ii = 0; ii < MAX_LASER; ii++){
         col_temp = invader_lasers[ii].col;
         page_temp = invader_lasers[ii].page;

         if(page_temp > 6){
            if((col_temp < set_tank_pos + 5) && (col_temp > set_tank_pos - 5) && invader_lasers[ii].active == 1){
               player_lives--;
               invader_lasers[ii].active = 0;
               break;
            }
         }
      }
   }


   /*
   * Function: Detect collision 
   * between a laser and a sprite
   * ---------------------------- 
   * Globals:
   *   unsigned int: left boundry of army block
   *   unsigned int: right boundry of army block
   *   unsigned char array: army block    
   *   laser lasers: array of lasers
   */
   void collision_detect(){
      int SPRITE_RATIO = 5042;
      int ii;
      unsigned long diff;
      unsigned long TEMP;
      TEMP = 100;
      collision_tank_detect();
      for(ii = 0; ii < MAX_LASER; ii++){
         if(lasers[ii].active){
               if(lasers[ii].page <= 0){
                  lasers[ii].active = 0;
               }
               else if(lasers[ii].page <= army_page_offset+1){
                  // The following if statement checks if the laser is in the same column as the army
                  if(lasers[ii].col > army_col_offset && lasers[ii].col < army_col_offset + (13 * (MAX_INVADERS/2))){
                     unsigned long col_temp = lasers[ii].col;
                     diff = (army_col_offset + (13 * (MAX_INVADERS/2)) - col_temp);
                     diff = diff * SPRITE_RATIO;
                     diff = MAX_INVADERS - (diff >> 16) - 1;
                     if(invader_array[diff] == 1){
                           invader_array[diff] = 0;
                           lasers[ii].active = 0;
                           player_score++;
                           
                     }
                  }
                  if(lasers[ii].col > army_col_offset && lasers[ii].col < army_col_offset + (13 * (MAX_INVADERS/2)) && lasers[ii].active == 1){
                     unsigned long col_temp = lasers[ii].col;
                     diff = (army_col_offset + (13 * (MAX_INVADERS/2)) - col_temp);
                     diff = diff * SPRITE_RATIO;
                     diff = MAX_INVADERS/2 - (diff >> 16) - 1;
                     if(invader_array[diff] == 1){
                           invader_array[diff] = 0;
                           lasers[ii].active = 0;
                           player_score++;
                           
                     }
                           
                  }
               }
         }
      }
   }

   /*
   * Function: add_invdaer_laser
   * ----------------------------
   * Adds a laser to the invader laser array
   * given the page and col 
   * Globals:
   *   laser lasers: array of lasers
   */
   void add_invader_laser(int page, int col)
   {
      int ii;
      for(ii = 0; ii < MAX_LASER; ii++){
         if(invader_lasers[ii].active == 0){
            invader_lasers[ii].active = 1;
            invader_lasers[ii].page = page;
            invader_lasers[ii].col = col;
            break;
         }
      }
   }

   /*
   * Function: Update invader lasers position
   * ----------------------------
   * Updates the position of the invader lasers by incrementing
   * the page by 1 and leaving the col the same
   * Globals:
   *   laser lasers: array of lasers
   */
   void update_invader_lasers()
   {
      int ii;
      for(ii = 0; ii < MAX_LASER; ii++){
         if(invader_lasers[ii].active == 1){
            screen[(invader_lasers[ii].page * 128) + invader_lasers[ii].col] = 0x00;
            invader_lasers[ii].page++;
            screen[(invader_lasers[ii].page * 128) + invader_lasers[ii].col] = 0xFF;
            if(invader_lasers[ii].page > 7){
               invader_lasers[ii].active = 0;
            }
         }
      }
   }

   /*
   * Function: A function for the code to call to
   * run and functions associated with the invaders
   * lasers
   * ----------------------------
   * Updates the position of the invader lasers by incrementing
   * the page by 1 and leaving the col the same
   * Globals:
   *   laser lasers: array of lasers
   *   army_page_offset: the page offset of the army
   *   army_col_offset: the col offset of the army
   */
   void invader_laser(){
      int random_pos = 1;
      add_invader_laser((int)army_page_offset+1, (int)army_col_offset + (13 * random_pos)+5);
   }





