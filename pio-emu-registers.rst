.. # WARNING: This sphinx documentation file was automatically
.. # created directly from documentation info the source code.
.. # DO NOT CHANGE THIS FILE, since changes will be lost upon
.. # its next update.
.. # This file was automatically created on:
.. # 2021-04-17T04:11:01.276260Z

PIO Emulator: List of Registers
===============================

The PIO emulator provides registers in addition to those
of the PIO as specified in the RP2040 datasheet to allow
for inspection of more details of the PIO's internal state
such as its scratch registers X and Y, its shift registers
ISR, OSR, FIFO memory, and read access to PIO instruction
memory for enhanced debugging of programs.
Base address for the PIO emulator register sets is
0x58200000 and 0x58300000 for PIO0 and PIO1, respectively.


.. csv-table:: PIO Emulator: List of Registers
   :header: Offset, Name, Info
   :widths: 8, 20, 40

   0x000, SM0_REGX, "Direct read / write access to the SM's scratch register X."
   0x004, SM0_REGY, "Direct read / write access to the SM's scratch register Y."
   0x008, SM0_PC, "Direct read-only access to the SM's instruction pointer / program counter."
   0x00c, SM0_ISR, "Direct read / write access to the SM's input shift register."
   0x010, SM0_ISR_SHIFT_COUNT, "Direct read / write access to the SM's input shift count register."
   0x014, SM0_OSR, "Direct read / write access to all of the SM's output shift register."
   0x018, SM0_OSR_SHIFT_COUNT, "Direct read / write access to the SM's output shift count register."
   0x01c, SM0_FIFO_MEM0, "Read / write access to FIFO memory word."
   0x020, SM0_FIFO_MEM1, "Read / write access to FIFO memory word."
   0x024, SM0_FIFO_MEM2, "Read / write access to FIFO memory word."
   0x028, SM0_FIFO_MEM3, "Read / write access to FIFO memory word."
   0x02c, SM0_FIFO_MEM4, "Read / write access to FIFO memory word."
   0x030, SM0_FIFO_MEM5, "Read / write access to FIFO memory word."
   0x034, SM0_FIFO_MEM6, "Read / write access to FIFO memory word."
   0x038, SM0_FIFO_MEM7, "Read / write access to FIFO memory word."
   0x03c, SM0_DELAY, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x040, SM0_DELAY_CYCLE, "Read-only access to the SM's delay status."
   0x044, SM0_PENDING_DELAY, "Direct read-only access to the SM's number of pending delay cycles."
   0x048, SM0_CLK_ENABLE, "Read-only access to the SM's delay status."
   0x04c, SM0_BREAKPOINTS, "Each bit of this values corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x050, SM0_TRACEPOINTS, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is printed to console output.  The message contains the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x054, SM1_REGX, "Direct read / write access to the SM's scratch register X."
   0x058, SM1_REGY, "Direct read / write access to the SM's scratch register Y."
   0x05c, SM1_PC, "Direct read-only access to the SM's instruction pointer / program counter."
   0x060, SM1_ISR, "Direct read / write access to the SM's input shift register."
   0x064, SM1_ISR_SHIFT_COUNT, "Direct read / write access to the SM's input shift count register."
   0x068, SM1_OSR, "Direct read / write access to all of the SM's output shift register."
   0x06c, SM1_OSR_SHIFT_COUNT, "Direct read / write access to the SM's output shift count register."
   0x070, SM1_FIFO_MEM0, "Read / write access to FIFO memory word."
   0x074, SM1_FIFO_MEM1, "Read / write access to FIFO memory word."
   0x078, SM1_FIFO_MEM2, "Read / write access to FIFO memory word."
   0x07c, SM1_FIFO_MEM3, "Read / write access to FIFO memory word."
   0x080, SM1_FIFO_MEM4, "Read / write access to FIFO memory word."
   0x084, SM1_FIFO_MEM5, "Read / write access to FIFO memory word."
   0x088, SM1_FIFO_MEM6, "Read / write access to FIFO memory word."
   0x08c, SM1_FIFO_MEM7, "Read / write access to FIFO memory word."
   0x090, SM1_DELAY, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x094, SM1_DELAY_CYCLE, "Read-only access to the SM's delay status."
   0x098, SM1_PENDING_DELAY, "Direct read-only access to the SM's number of pending delay cycles."
   0x09c, SM1_CLK_ENABLE, "Read-only access to the SM's delay status."
   0x0a0, SM1_BREAKPOINTS, "Each bit of this values corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x0a4, SM1_TRACEPOINTS, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is printed to console output.  The message contains the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x0a8, SM2_REGX, "Direct read / write access to the SM's scratch register X."
   0x0ac, SM2_REGY, "Direct read / write access to the SM's scratch register Y."
   0x0b0, SM2_PC, "Direct read-only access to the SM's instruction pointer / program counter."
   0x0b4, SM2_ISR, "Direct read / write access to the SM's input shift register."
   0x0b8, SM2_ISR_SHIFT_COUNT, "Direct read / write access to the SM's input shift count register."
   0x0bc, SM2_OSR, "Direct read / write access to all of the SM's output shift register."
   0x0c0, SM2_OSR_SHIFT_COUNT, "Direct read / write access to the SM's output shift count register."
   0x0c4, SM2_FIFO_MEM0, "Read / write access to FIFO memory word."
   0x0c8, SM2_FIFO_MEM1, "Read / write access to FIFO memory word."
   0x0cc, SM2_FIFO_MEM2, "Read / write access to FIFO memory word."
   0x0d0, SM2_FIFO_MEM3, "Read / write access to FIFO memory word."
   0x0d4, SM2_FIFO_MEM4, "Read / write access to FIFO memory word."
   0x0d8, SM2_FIFO_MEM5, "Read / write access to FIFO memory word."
   0x0dc, SM2_FIFO_MEM6, "Read / write access to FIFO memory word."
   0x0e0, SM2_FIFO_MEM7, "Read / write access to FIFO memory word."
   0x0e4, SM2_DELAY, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x0e8, SM2_DELAY_CYCLE, "Read-only access to the SM's delay status."
   0x0ec, SM2_PENDING_DELAY, "Direct read-only access to the SM's number of pending delay cycles."
   0x0f0, SM2_CLK_ENABLE, "Read-only access to the SM's delay status."
   0x0f4, SM2_BREAKPOINTS, "Each bit of this values corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x0f8, SM2_TRACEPOINTS, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is printed to console output.  The message contains the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x0fc, SM3_REGX, "Direct read / write access to the SM's scratch register X."
   0x100, SM3_REGY, "Direct read / write access to the SM's scratch register Y."
   0x104, SM3_PC, "Direct read-only access to the SM's instruction pointer / program counter."
   0x108, SM3_ISR, "Direct read / write access to the SM's input shift register."
   0x10c, SM3_ISR_SHIFT_COUNT, "Direct read / write access to the SM's input shift count register."
   0x110, SM3_OSR, "Direct read / write access to all of the SM's output shift register."
   0x114, SM3_OSR_SHIFT_COUNT, "Direct read / write access to the SM's output shift count register."
   0x118, SM3_FIFO_MEM0, "Read / write access to FIFO memory word."
   0x11c, SM3_FIFO_MEM1, "Read / write access to FIFO memory word."
   0x120, SM3_FIFO_MEM2, "Read / write access to FIFO memory word."
   0x124, SM3_FIFO_MEM3, "Read / write access to FIFO memory word."
   0x128, SM3_FIFO_MEM4, "Read / write access to FIFO memory word."
   0x12c, SM3_FIFO_MEM5, "Read / write access to FIFO memory word."
   0x130, SM3_FIFO_MEM6, "Read / write access to FIFO memory word."
   0x134, SM3_FIFO_MEM7, "Read / write access to FIFO memory word."
   0x138, SM3_DELAY, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x13c, SM3_DELAY_CYCLE, "Read-only access to the SM's delay status."
   0x140, SM3_PENDING_DELAY, "Direct read-only access to the SM's number of pending delay cycles."
   0x144, SM3_CLK_ENABLE, "Read-only access to the SM's delay status."
   0x148, SM3_BREAKPOINTS, "Each bit of this values corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x14c, SM3_TRACEPOINTS, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is printed to console output.  The message contains the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x150, INSTR_MEM0, "Read / write access to instruction memory word."
   0x154, INSTR_MEM1, "Read / write access to instruction memory word."
   0x158, INSTR_MEM2, "Read / write access to instruction memory word."
   0x15c, INSTR_MEM3, "Read / write access to instruction memory word."
   0x160, INSTR_MEM4, "Read / write access to instruction memory word."
   0x164, INSTR_MEM5, "Read / write access to instruction memory word."
   0x168, INSTR_MEM6, "Read / write access to instruction memory word."
   0x16c, INSTR_MEM7, "Read / write access to instruction memory word."
   0x170, INSTR_MEM8, "Read / write access to instruction memory word."
   0x174, INSTR_MEM9, "Read / write access to instruction memory word."
   0x178, INSTR_MEM10, "Read / write access to instruction memory word."
   0x17c, INSTR_MEM11, "Read / write access to instruction memory word."
   0x180, INSTR_MEM12, "Read / write access to instruction memory word."
   0x184, INSTR_MEM13, "Read / write access to instruction memory word."
   0x188, INSTR_MEM14, "Read / write access to instruction memory word."
   0x18c, INSTR_MEM15, "Read / write access to instruction memory word."
   0x190, INSTR_MEM16, "Read / write access to instruction memory word."
   0x194, INSTR_MEM17, "Read / write access to instruction memory word."
   0x198, INSTR_MEM18, "Read / write access to instruction memory word."
   0x19c, INSTR_MEM19, "Read / write access to instruction memory word."
   0x1a0, INSTR_MEM20, "Read / write access to instruction memory word."
   0x1a4, INSTR_MEM21, "Read / write access to instruction memory word."
   0x1a8, INSTR_MEM22, "Read / write access to instruction memory word."
   0x1ac, INSTR_MEM23, "Read / write access to instruction memory word."
   0x1b0, INSTR_MEM24, "Read / write access to instruction memory word."
   0x1b4, INSTR_MEM25, "Read / write access to instruction memory word."
   0x1b8, INSTR_MEM26, "Read / write access to instruction memory word."
   0x1bc, INSTR_MEM27, "Read / write access to instruction memory word."
   0x1c0, INSTR_MEM28, "Read / write access to instruction memory word."
   0x1c4, INSTR_MEM29, "Read / write access to instruction memory word."
   0x1c8, INSTR_MEM30, "Read / write access to instruction memory word."
   0x1cc, INSTR_MEM31, "Read / write access to instruction memory word."
   0x1d0, GPIO_PINS, "Direct read / write access to all of the 32 GPIO pins."
   0x1d4, GPIO_PINDIRS, "Direct read / write access to all of the 32 GPIO pin directions."

PIO Emulator: SM0_ISR, SM1_ISR, SM2_ISR, SM3_ISR
------------------------------------------------

Offsets: 0x00c, 0x060, 0x0b4, 0x108

.. csv-table:: PIO Emulator: SM0_ISR, SM1_ISR, SM2_ISR, SM3_ISR
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's input shift register.", RW, 0

PIO Emulator: SM0_CLK_ENABLE, SM1_CLK_ENABLE, SM2_CLK_ENABLE, SM3_CLK_ENABLE
----------------------------------------------------------------------------

Offsets: 0x048, 0x09c, 0x0f0, 0x144

.. csv-table:: PIO Emulator: SM0_CLK_ENABLE, SM1_CLK_ENABLE, SM2_CLK_ENABLE, SM3_CLK_ENABLE
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:1, Reserved., "―", ―, ―
   0, DELAY_CYCLE, "0x1, if in the current cycle the clock enable signal evaluates to 0x1.", RO, 0

PIO Emulator: SM0_REGX, SM1_REGX, SM2_REGX, SM3_REGX
----------------------------------------------------

Offsets: 0x000, 0x054, 0x0a8, 0x0fc

.. csv-table:: PIO Emulator: SM0_REGX, SM1_REGX, SM2_REGX, SM3_REGX
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's scratch register X.", RW, 0

PIO Emulator: GPIO_PINS
-----------------------

Offset: 0x1d0

.. csv-table:: PIO Emulator: GPIO_PINS
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, GPIO_PIN31, "0x1 for HIGH or 0x0 for LOW", RW, 0
   30, GPIO_PIN30, "0x1 for HIGH or 0x0 for LOW", RW, 0
   29, GPIO_PIN29, "0x1 for HIGH or 0x0 for LOW", RW, 0
   28, GPIO_PIN28, "0x1 for HIGH or 0x0 for LOW", RW, 0
   27, GPIO_PIN27, "0x1 for HIGH or 0x0 for LOW", RW, 0
   26, GPIO_PIN26, "0x1 for HIGH or 0x0 for LOW", RW, 0
   25, GPIO_PIN25, "0x1 for HIGH or 0x0 for LOW", RW, 0
   24, GPIO_PIN24, "0x1 for HIGH or 0x0 for LOW", RW, 0
   23, GPIO_PIN23, "0x1 for HIGH or 0x0 for LOW", RW, 0
   22, GPIO_PIN22, "0x1 for HIGH or 0x0 for LOW", RW, 0
   21, GPIO_PIN21, "0x1 for HIGH or 0x0 for LOW", RW, 0
   20, GPIO_PIN20, "0x1 for HIGH or 0x0 for LOW", RW, 0
   19, GPIO_PIN19, "0x1 for HIGH or 0x0 for LOW", RW, 0
   18, GPIO_PIN18, "0x1 for HIGH or 0x0 for LOW", RW, 0
   17, GPIO_PIN17, "0x1 for HIGH or 0x0 for LOW", RW, 0
   16, GPIO_PIN16, "0x1 for HIGH or 0x0 for LOW", RW, 0
   15, GPIO_PIN15, "0x1 for HIGH or 0x0 for LOW", RW, 0
   14, GPIO_PIN14, "0x1 for HIGH or 0x0 for LOW", RW, 0
   13, GPIO_PIN13, "0x1 for HIGH or 0x0 for LOW", RW, 0
   12, GPIO_PIN12, "0x1 for HIGH or 0x0 for LOW", RW, 0
   11, GPIO_PIN11, "0x1 for HIGH or 0x0 for LOW", RW, 0
   10, GPIO_PIN10, "0x1 for HIGH or 0x0 for LOW", RW, 0
   9, GPIO_PIN9, "0x1 for HIGH or 0x0 for LOW", RW, 0
   8, GPIO_PIN8, "0x1 for HIGH or 0x0 for LOW", RW, 0
   7, GPIO_PIN7, "0x1 for HIGH or 0x0 for LOW", RW, 0
   6, GPIO_PIN6, "0x1 for HIGH or 0x0 for LOW", RW, 0
   5, GPIO_PIN5, "0x1 for HIGH or 0x0 for LOW", RW, 0
   4, GPIO_PIN4, "0x1 for HIGH or 0x0 for LOW", RW, 0
   3, GPIO_PIN3, "0x1 for HIGH or 0x0 for LOW", RW, 0
   2, GPIO_PIN2, "0x1 for HIGH or 0x0 for LOW", RW, 0
   1, GPIO_PIN1, "0x1 for HIGH or 0x0 for LOW", RW, 0
   0, GPIO_PIN0, "0x1 for HIGH or 0x0 for LOW", RW, 0

PIO Emulator: SM0_OSR, SM1_OSR, SM2_OSR, SM3_OSR
------------------------------------------------

Offsets: 0x014, 0x068, 0x0bc, 0x110

.. csv-table:: PIO Emulator: SM0_OSR, SM1_OSR, SM2_OSR, SM3_OSR
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to all of the SM's output shift register.", RW, 0

PIO Emulator: SM0_ISR_SHIFT_COUNT, SM1_ISR_SHIFT_COUNT, SM2_ISR_SHIFT_COUNT, SM3_ISR_SHIFT_COUNT
------------------------------------------------------------------------------------------------

Offsets: 0x010, 0x064, 0x0b8, 0x10c

.. csv-table:: PIO Emulator: SM0_ISR_SHIFT_COUNT, SM1_ISR_SHIFT_COUNT, SM2_ISR_SHIFT_COUNT, SM3_ISR_SHIFT_COUNT
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's input shift count register.", RW, 0

PIO Emulator: SM0_TRACEPOINTS, SM1_TRACEPOINTS, SM2_TRACEPOINTS, SM3_TRACEPOINTS
--------------------------------------------------------------------------------

Offsets: 0x050, 0x0a4, 0x0f8, 0x14c

.. csv-table:: PIO Emulator: SM0_TRACEPOINTS, SM1_TRACEPOINTS, SM2_TRACEPOINTS, SM3_TRACEPOINTS
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, TP_MEM31, "0x1, if the memory address is marked as tracepoint", RW, 0
   30, TP_MEM30, "0x1, if the memory address is marked as tracepoint", RW, 0
   29, TP_MEM29, "0x1, if the memory address is marked as tracepoint", RW, 0
   28, TP_MEM28, "0x1, if the memory address is marked as tracepoint", RW, 0
   27, TP_MEM27, "0x1, if the memory address is marked as tracepoint", RW, 0
   26, TP_MEM26, "0x1, if the memory address is marked as tracepoint", RW, 0
   25, TP_MEM25, "0x1, if the memory address is marked as tracepoint", RW, 0
   24, TP_MEM24, "0x1, if the memory address is marked as tracepoint", RW, 0
   23, TP_MEM23, "0x1, if the memory address is marked as tracepoint", RW, 0
   22, TP_MEM22, "0x1, if the memory address is marked as tracepoint", RW, 0
   21, TP_MEM21, "0x1, if the memory address is marked as tracepoint", RW, 0
   20, TP_MEM20, "0x1, if the memory address is marked as tracepoint", RW, 0
   19, TP_MEM19, "0x1, if the memory address is marked as tracepoint", RW, 0
   18, TP_MEM18, "0x1, if the memory address is marked as tracepoint", RW, 0
   17, TP_MEM17, "0x1, if the memory address is marked as tracepoint", RW, 0
   16, TP_MEM16, "0x1, if the memory address is marked as tracepoint", RW, 0
   15, TP_MEM15, "0x1, if the memory address is marked as tracepoint", RW, 0
   14, TP_MEM14, "0x1, if the memory address is marked as tracepoint", RW, 0
   13, TP_MEM13, "0x1, if the memory address is marked as tracepoint", RW, 0
   12, TP_MEM12, "0x1, if the memory address is marked as tracepoint", RW, 0
   11, TP_MEM11, "0x1, if the memory address is marked as tracepoint", RW, 0
   10, TP_MEM10, "0x1, if the memory address is marked as tracepoint", RW, 0
   9, TP_MEM9, "0x1, if the memory address is marked as tracepoint", RW, 0
   8, TP_MEM8, "0x1, if the memory address is marked as tracepoint", RW, 0
   7, TP_MEM7, "0x1, if the memory address is marked as tracepoint", RW, 0
   6, TP_MEM6, "0x1, if the memory address is marked as tracepoint", RW, 0
   5, TP_MEM5, "0x1, if the memory address is marked as tracepoint", RW, 0
   4, TP_MEM4, "0x1, if the memory address is marked as tracepoint", RW, 0
   3, TP_MEM3, "0x1, if the memory address is marked as tracepoint", RW, 0
   2, TP_MEM2, "0x1, if the memory address is marked as tracepoint", RW, 0
   1, TP_MEM1, "0x1, if the memory address is marked as tracepoint", RW, 0
   0, TP_MEM0, "0x1, if the memory address is marked as tracepoint", RW, 0

PIO Emulator: INSTR_MEM0, INSTR_MEM1, INSTR_MEM2, INSTR_MEM3, INSTR_MEM4, INSTR_MEM5, INSTR_MEM6, INSTR_MEM7, INSTR_MEM8, INSTR_MEM9, INSTR_MEM10, INSTR_MEM11, INSTR_MEM12, INSTR_MEM13, INSTR_MEM14, INSTR_MEM15, INSTR_MEM16, INSTR_MEM17, INSTR_MEM18, INSTR_MEM19, INSTR_MEM20, INSTR_MEM21, INSTR_MEM22, INSTR_MEM23, INSTR_MEM24, INSTR_MEM25, INSTR_MEM26, INSTR_MEM27, INSTR_MEM28, INSTR_MEM29, INSTR_MEM30, INSTR_MEM31
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Offsets: 0x150, 0x154, 0x158, 0x15c, 0x160, 0x164, 0x168, 0x16c, 0x170, 0x174, 0x178, 0x17c, 0x180, 0x184, 0x188, 0x18c, 0x190, 0x194, 0x198, 0x19c, 0x1a0, 0x1a4, 0x1a8, 0x1ac, 0x1b0, 0x1b4, 0x1b8, 0x1bc, 0x1c0, 0x1c4, 0x1c8, 0x1cc

.. csv-table:: PIO Emulator: INSTR_MEM0, INSTR_MEM1, INSTR_MEM2, INSTR_MEM3, INSTR_MEM4, INSTR_MEM5, INSTR_MEM6, INSTR_MEM7, INSTR_MEM8, INSTR_MEM9, INSTR_MEM10, INSTR_MEM11, INSTR_MEM12, INSTR_MEM13, INSTR_MEM14, INSTR_MEM15, INSTR_MEM16, INSTR_MEM17, INSTR_MEM18, INSTR_MEM19, INSTR_MEM20, INSTR_MEM21, INSTR_MEM22, INSTR_MEM23, INSTR_MEM24, INSTR_MEM25, INSTR_MEM26, INSTR_MEM27, INSTR_MEM28, INSTR_MEM29, INSTR_MEM30, INSTR_MEM31
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Read / write access to instruction memory word.", RW, 0

PIO Emulator: SM0_OSR_SHIFT_COUNT, SM1_OSR_SHIFT_COUNT, SM2_OSR_SHIFT_COUNT, SM3_OSR_SHIFT_COUNT
------------------------------------------------------------------------------------------------

Offsets: 0x018, 0x06c, 0x0c0, 0x114

.. csv-table:: PIO Emulator: SM0_OSR_SHIFT_COUNT, SM1_OSR_SHIFT_COUNT, SM2_OSR_SHIFT_COUNT, SM3_OSR_SHIFT_COUNT
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's output shift count register.", RW, 0

PIO Emulator: SM0_PC, SM1_PC, SM2_PC, SM3_PC
--------------------------------------------

Offsets: 0x008, 0x05c, 0x0b0, 0x104

.. csv-table:: PIO Emulator: SM0_PC, SM1_PC, SM2_PC, SM3_PC
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read-only access to the SM's instruction pointer / program counter.", RW, 0

PIO Emulator: SM0_REGY, SM1_REGY, SM2_REGY, SM3_REGY
----------------------------------------------------

Offsets: 0x004, 0x058, 0x0ac, 0x100

.. csv-table:: PIO Emulator: SM0_REGY, SM1_REGY, SM2_REGY, SM3_REGY
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's scratch register Y.", RW, 0

PIO Emulator: SM0_DELAY_CYCLE, SM1_DELAY_CYCLE, SM2_DELAY_CYCLE, SM3_DELAY_CYCLE
--------------------------------------------------------------------------------

Offsets: 0x040, 0x094, 0x0e8, 0x13c

.. csv-table:: PIO Emulator: SM0_DELAY_CYCLE, SM1_DELAY_CYCLE, SM2_DELAY_CYCLE, SM3_DELAY_CYCLE
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:1, Reserved., "―", ―, ―
   0, DELAY_CYCLE, "0x1, if the currently executed cycles is a delay cycle.", RO, 0

PIO Emulator: GPIO_PINDIRS
--------------------------

Offset: 0x1d4

.. csv-table:: PIO Emulator: GPIO_PINDIRS
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, GPIO_PINDIR31, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   30, GPIO_PINDIR30, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   29, GPIO_PINDIR29, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   28, GPIO_PINDIR28, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   27, GPIO_PINDIR27, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   26, GPIO_PINDIR26, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   25, GPIO_PINDIR25, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   24, GPIO_PINDIR24, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   23, GPIO_PINDIR23, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   22, GPIO_PINDIR22, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   21, GPIO_PINDIR21, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   20, GPIO_PINDIR20, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   19, GPIO_PINDIR19, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   18, GPIO_PINDIR18, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   17, GPIO_PINDIR17, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   16, GPIO_PINDIR16, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   15, GPIO_PINDIR15, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   14, GPIO_PINDIR14, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   13, GPIO_PINDIR13, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   12, GPIO_PINDIR12, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   11, GPIO_PINDIR11, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   10, GPIO_PINDIR10, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   9, GPIO_PINDIR9, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   8, GPIO_PINDIR8, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   7, GPIO_PINDIR7, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   6, GPIO_PINDIR6, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   5, GPIO_PINDIR5, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   4, GPIO_PINDIR4, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   3, GPIO_PINDIR3, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   2, GPIO_PINDIR2, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   1, GPIO_PINDIR1, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0
   0, GPIO_PINDIR0, "0x1 for pin direction out or 0x0 for pin direction in", RW, 0

PIO Emulator: SM0_FIFO_MEM0, SM0_FIFO_MEM1, SM0_FIFO_MEM2, SM0_FIFO_MEM3, SM0_FIFO_MEM4, SM0_FIFO_MEM5, SM0_FIFO_MEM6, SM0_FIFO_MEM7, SM1_FIFO_MEM0, SM1_FIFO_MEM1, SM1_FIFO_MEM2, SM1_FIFO_MEM3, SM1_FIFO_MEM4, SM1_FIFO_MEM5, SM1_FIFO_MEM6, SM1_FIFO_MEM7, SM2_FIFO_MEM0, SM2_FIFO_MEM1, SM2_FIFO_MEM2, SM2_FIFO_MEM3, SM2_FIFO_MEM4, SM2_FIFO_MEM5, SM2_FIFO_MEM6, SM2_FIFO_MEM7, SM3_FIFO_MEM0, SM3_FIFO_MEM1, SM3_FIFO_MEM2, SM3_FIFO_MEM3, SM3_FIFO_MEM4, SM3_FIFO_MEM5, SM3_FIFO_MEM6, SM3_FIFO_MEM7
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Offsets: 0x01c, 0x020, 0x024, 0x028, 0x02c, 0x030, 0x034, 0x038, 0x070, 0x074, 0x078, 0x07c, 0x080, 0x084, 0x088, 0x08c, 0x0c4, 0x0c8, 0x0cc, 0x0d0, 0x0d4, 0x0d8, 0x0dc, 0x0e0, 0x118, 0x11c, 0x120, 0x124, 0x128, 0x12c, 0x130, 0x134

.. csv-table:: PIO Emulator: SM0_FIFO_MEM0, SM0_FIFO_MEM1, SM0_FIFO_MEM2, SM0_FIFO_MEM3, SM0_FIFO_MEM4, SM0_FIFO_MEM5, SM0_FIFO_MEM6, SM0_FIFO_MEM7, SM1_FIFO_MEM0, SM1_FIFO_MEM1, SM1_FIFO_MEM2, SM1_FIFO_MEM3, SM1_FIFO_MEM4, SM1_FIFO_MEM5, SM1_FIFO_MEM6, SM1_FIFO_MEM7, SM2_FIFO_MEM0, SM2_FIFO_MEM1, SM2_FIFO_MEM2, SM2_FIFO_MEM3, SM2_FIFO_MEM4, SM2_FIFO_MEM5, SM2_FIFO_MEM6, SM2_FIFO_MEM7, SM3_FIFO_MEM0, SM3_FIFO_MEM1, SM3_FIFO_MEM2, SM3_FIFO_MEM3, SM3_FIFO_MEM4, SM3_FIFO_MEM5, SM3_FIFO_MEM6, SM3_FIFO_MEM7
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Read / write access to FIFO memory word.", RW, 0

PIO Emulator: SM0_DELAY, SM1_DELAY, SM2_DELAY, SM3_DELAY
--------------------------------------------------------

Offsets: 0x03c, 0x090, 0x0e4, 0x138

.. csv-table:: PIO Emulator: SM0_DELAY, SM1_DELAY, SM2_DELAY, SM3_DELAY
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:5, Reserved., "―", ―, ―
   4:0, ―, "Direct read-only access to the SM's currently executed instruction's number of delay cycles.", RO, 0

PIO Emulator: SM0_BREAKPOINTS, SM1_BREAKPOINTS, SM2_BREAKPOINTS, SM3_BREAKPOINTS
--------------------------------------------------------------------------------

Offsets: 0x04c, 0x0a0, 0x0f4, 0x148

.. csv-table:: PIO Emulator: SM0_BREAKPOINTS, SM1_BREAKPOINTS, SM2_BREAKPOINTS, SM3_BREAKPOINTS
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, BP_MEM31, "0x1, if the memory address is marked as breakpoint", RW, 0
   30, BP_MEM30, "0x1, if the memory address is marked as breakpoint", RW, 0
   29, BP_MEM29, "0x1, if the memory address is marked as breakpoint", RW, 0
   28, BP_MEM28, "0x1, if the memory address is marked as breakpoint", RW, 0
   27, BP_MEM27, "0x1, if the memory address is marked as breakpoint", RW, 0
   26, BP_MEM26, "0x1, if the memory address is marked as breakpoint", RW, 0
   25, BP_MEM25, "0x1, if the memory address is marked as breakpoint", RW, 0
   24, BP_MEM24, "0x1, if the memory address is marked as breakpoint", RW, 0
   23, BP_MEM23, "0x1, if the memory address is marked as breakpoint", RW, 0
   22, BP_MEM22, "0x1, if the memory address is marked as breakpoint", RW, 0
   21, BP_MEM21, "0x1, if the memory address is marked as breakpoint", RW, 0
   20, BP_MEM20, "0x1, if the memory address is marked as breakpoint", RW, 0
   19, BP_MEM19, "0x1, if the memory address is marked as breakpoint", RW, 0
   18, BP_MEM18, "0x1, if the memory address is marked as breakpoint", RW, 0
   17, BP_MEM17, "0x1, if the memory address is marked as breakpoint", RW, 0
   16, BP_MEM16, "0x1, if the memory address is marked as breakpoint", RW, 0
   15, BP_MEM15, "0x1, if the memory address is marked as breakpoint", RW, 0
   14, BP_MEM14, "0x1, if the memory address is marked as breakpoint", RW, 0
   13, BP_MEM13, "0x1, if the memory address is marked as breakpoint", RW, 0
   12, BP_MEM12, "0x1, if the memory address is marked as breakpoint", RW, 0
   11, BP_MEM11, "0x1, if the memory address is marked as breakpoint", RW, 0
   10, BP_MEM10, "0x1, if the memory address is marked as breakpoint", RW, 0
   9, BP_MEM9, "0x1, if the memory address is marked as breakpoint", RW, 0
   8, BP_MEM8, "0x1, if the memory address is marked as breakpoint", RW, 0
   7, BP_MEM7, "0x1, if the memory address is marked as breakpoint", RW, 0
   6, BP_MEM6, "0x1, if the memory address is marked as breakpoint", RW, 0
   5, BP_MEM5, "0x1, if the memory address is marked as breakpoint", RW, 0
   4, BP_MEM4, "0x1, if the memory address is marked as breakpoint", RW, 0
   3, BP_MEM3, "0x1, if the memory address is marked as breakpoint", RW, 0
   2, BP_MEM2, "0x1, if the memory address is marked as breakpoint", RW, 0
   1, BP_MEM1, "0x1, if the memory address is marked as breakpoint", RW, 0
   0, BP_MEM0, "0x1, if the memory address is marked as breakpoint", RW, 0

PIO Emulator: SM0_PENDING_DELAY, SM1_PENDING_DELAY, SM2_PENDING_DELAY, SM3_PENDING_DELAY
----------------------------------------------------------------------------------------

Offsets: 0x044, 0x098, 0x0ec, 0x140

.. csv-table:: PIO Emulator: SM0_PENDING_DELAY, SM1_PENDING_DELAY, SM2_PENDING_DELAY, SM3_PENDING_DELAY
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:5, Reserved., "―", ―, ―
   4:0, PENDING_DELAY, "number (0..0x1f) of pending delays of the currently executed instruction", RO, 0

