.. # WARNING: This sphinx documentation file was automatically
.. # created directly from documentation info in the source code.
.. # DO NOT CHANGE THIS FILE, since changes will be lost upon
.. # its next update.  Instead, change the info in the source code.
.. # This file was automatically created on:
.. # 2021-06-04T16:35:16.519111Z

.. _section-top_emulator_pio_registers:

.. index::
   single: Emulator PIO Registers
   single: registers set; Emulator PIO Registers

Emulator PIO Registers
======================

List of Registers
-----------------

The PIO emulator provides registers in addition to those
of the PIO as specified in the RP2040 datasheet to allow
for inspection of more details of the PIO's internal state
such as its scratch registers X and Y, its shift registers
ISR, OSR, FIFO memory, and read access to PIO instruction
memory for enhanced debugging of programs.
Base address for the two emulator PIO register sets (one 
register set for each of the two PIOs) is
0x58200000 and 0x58300000 for PIO0 and PIO1, respectively.


.. csv-table::
   :header: Offset, Name, Info
   :widths: 8, 20, 40

   0x000, :ref:`SM0_REGX <SM0_REGX-details-label>`, "Direct read / write access to the SM's scratch register X."
   0x004, :ref:`SM0_REGY <SM0_REGY-details-label>`, "Direct read / write access to the SM's scratch register Y."
   0x008, :ref:`SM0_PC <SM0_PC-details-label>`, "Direct read / write access to the SM's instruction pointer / program counter."
   0x00c, :ref:`SM0_ISR <SM0_ISR-details-label>`, "Direct read / write access to the SM's input shift register."
   0x010, :ref:`SM0_ISR_SHIFT_COUNT <SM0_ISR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's input shift count register."
   0x014, :ref:`SM0_OSR <SM0_OSR-details-label>`, "Direct read / write access to all of the SM's output shift register."
   0x018, :ref:`SM0_OSR_SHIFT_COUNT <SM0_OSR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's output shift count register."
   0x01c, :ref:`SM0_FIFO_MEM0 <SM0_FIFO_MEM0-details-label>`, "Read / write access to FIFO memory word."
   0x020, :ref:`SM0_FIFO_MEM1 <SM0_FIFO_MEM1-details-label>`, "Read / write access to FIFO memory word."
   0x024, :ref:`SM0_FIFO_MEM2 <SM0_FIFO_MEM2-details-label>`, "Read / write access to FIFO memory word."
   0x028, :ref:`SM0_FIFO_MEM3 <SM0_FIFO_MEM3-details-label>`, "Read / write access to FIFO memory word."
   0x02c, :ref:`SM0_FIFO_MEM4 <SM0_FIFO_MEM4-details-label>`, "Read / write access to FIFO memory word."
   0x030, :ref:`SM0_FIFO_MEM5 <SM0_FIFO_MEM5-details-label>`, "Read / write access to FIFO memory word."
   0x034, :ref:`SM0_FIFO_MEM6 <SM0_FIFO_MEM6-details-label>`, "Read / write access to FIFO memory word."
   0x038, :ref:`SM0_FIFO_MEM7 <SM0_FIFO_MEM7-details-label>`, "Read / write access to FIFO memory word."
   0x03c, :ref:`SM0_CLEAR_FORCED <SM0_CLEAR_FORCED-details-label>`, "When writing to this address, any pending forced instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x040, :ref:`SM0_CLEAR_EXECD <SM0_CLEAR_EXECD-details-label>`, "When writing to this address, any pending EXEC'd instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x044, :ref:`SM0_INSTR_ORIGIN <SM0_INSTR_ORIGIN-details-label>`, "Direct read-only access to the origin of the SM's currently executed instruction.  The mode bits determine the origin category.  If the origin category is memory address, the memory address bits will contain the memory instruction's address. Otherwise, the bits of the memory address are undefined. Note that for memory instructions, the address may differ from the value of the instruction pointer PC, if the PC has already been updated while the instruction is still in progress."
   0x048, :ref:`SM0_DELAY <SM0_DELAY-details-label>`, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x04c, :ref:`SM0_DELAY_CYCLE <SM0_DELAY_CYCLE-details-label>`, "Read-only access to the SM's delay status."
   0x050, :ref:`SM0_PENDING_DELAY <SM0_PENDING_DELAY-details-label>`, "Direct read-only access to the SM's number of pending delay cycles."
   0x054, :ref:`SM0_FORCED_INSTR <SM0_FORCED_INSTR-details-label>`, "Direct read-only access to the op-code of a forced instruction that is awaiting execution during the next clock cycle.  For writing a forced instruction, use SMx_INSTR of PIORegisters instead."
   0x058, :ref:`SM0_EXECD_INSTR <SM0_EXECD_INSTR-details-label>`, "Direct read/write access to the op-code of an EXEC'd instruction that is awaiting execution during the next clock cycle, unless the state machine's clock signal does not evaluate to true, or there is a pending forced instruction, in which case the forced instruction will be executed first."
   0x05c, :ref:`SM0_CLK_ENABLE <SM0_CLK_ENABLE-details-label>`, "Read-only access to the SM's delay status."
   0x060, :ref:`SM0_BREAKPOINTS <SM0_BREAKPOINTS-details-label>`, "Each bit of this value corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x064, :ref:`SM0_TRACEPOINTS <SM0_TRACEPOINTS-details-label>`, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is typically printed to console output (depending on the specific client application).  The message may, for example, caontain the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x068, :ref:`SM1_REGX <SM1_REGX-details-label>`, "Direct read / write access to the SM's scratch register X."
   0x06c, :ref:`SM1_REGY <SM1_REGY-details-label>`, "Direct read / write access to the SM's scratch register Y."
   0x070, :ref:`SM1_PC <SM1_PC-details-label>`, "Direct read / write access to the SM's instruction pointer / program counter."
   0x074, :ref:`SM1_ISR <SM1_ISR-details-label>`, "Direct read / write access to the SM's input shift register."
   0x078, :ref:`SM1_ISR_SHIFT_COUNT <SM1_ISR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's input shift count register."
   0x07c, :ref:`SM1_OSR <SM1_OSR-details-label>`, "Direct read / write access to all of the SM's output shift register."
   0x080, :ref:`SM1_OSR_SHIFT_COUNT <SM1_OSR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's output shift count register."
   0x084, :ref:`SM1_FIFO_MEM0 <SM1_FIFO_MEM0-details-label>`, "Read / write access to FIFO memory word."
   0x088, :ref:`SM1_FIFO_MEM1 <SM1_FIFO_MEM1-details-label>`, "Read / write access to FIFO memory word."
   0x08c, :ref:`SM1_FIFO_MEM2 <SM1_FIFO_MEM2-details-label>`, "Read / write access to FIFO memory word."
   0x090, :ref:`SM1_FIFO_MEM3 <SM1_FIFO_MEM3-details-label>`, "Read / write access to FIFO memory word."
   0x094, :ref:`SM1_FIFO_MEM4 <SM1_FIFO_MEM4-details-label>`, "Read / write access to FIFO memory word."
   0x098, :ref:`SM1_FIFO_MEM5 <SM1_FIFO_MEM5-details-label>`, "Read / write access to FIFO memory word."
   0x09c, :ref:`SM1_FIFO_MEM6 <SM1_FIFO_MEM6-details-label>`, "Read / write access to FIFO memory word."
   0x0a0, :ref:`SM1_FIFO_MEM7 <SM1_FIFO_MEM7-details-label>`, "Read / write access to FIFO memory word."
   0x0a4, :ref:`SM1_CLEAR_FORCED <SM1_CLEAR_FORCED-details-label>`, "When writing to this address, any pending forced instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x0a8, :ref:`SM1_CLEAR_EXECD <SM1_CLEAR_EXECD-details-label>`, "When writing to this address, any pending EXEC'd instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x0ac, :ref:`SM1_INSTR_ORIGIN <SM1_INSTR_ORIGIN-details-label>`, "Direct read-only access to the origin of the SM's currently executed instruction.  The mode bits determine the origin category.  If the origin category is memory address, the memory address bits will contain the memory instruction's address. Otherwise, the bits of the memory address are undefined. Note that for memory instructions, the address may differ from the value of the instruction pointer PC, if the PC has already been updated while the instruction is still in progress."
   0x0b0, :ref:`SM1_DELAY <SM1_DELAY-details-label>`, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x0b4, :ref:`SM1_DELAY_CYCLE <SM1_DELAY_CYCLE-details-label>`, "Read-only access to the SM's delay status."
   0x0b8, :ref:`SM1_PENDING_DELAY <SM1_PENDING_DELAY-details-label>`, "Direct read-only access to the SM's number of pending delay cycles."
   0x0bc, :ref:`SM1_FORCED_INSTR <SM1_FORCED_INSTR-details-label>`, "Direct read-only access to the op-code of a forced instruction that is awaiting execution during the next clock cycle.  For writing a forced instruction, use SMx_INSTR of PIORegisters instead."
   0x0c0, :ref:`SM1_EXECD_INSTR <SM1_EXECD_INSTR-details-label>`, "Direct read/write access to the op-code of an EXEC'd instruction that is awaiting execution during the next clock cycle, unless the state machine's clock signal does not evaluate to true, or there is a pending forced instruction, in which case the forced instruction will be executed first."
   0x0c4, :ref:`SM1_CLK_ENABLE <SM1_CLK_ENABLE-details-label>`, "Read-only access to the SM's delay status."
   0x0c8, :ref:`SM1_BREAKPOINTS <SM1_BREAKPOINTS-details-label>`, "Each bit of this value corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x0cc, :ref:`SM1_TRACEPOINTS <SM1_TRACEPOINTS-details-label>`, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is typically printed to console output (depending on the specific client application).  The message may, for example, caontain the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x0d0, :ref:`SM2_REGX <SM2_REGX-details-label>`, "Direct read / write access to the SM's scratch register X."
   0x0d4, :ref:`SM2_REGY <SM2_REGY-details-label>`, "Direct read / write access to the SM's scratch register Y."
   0x0d8, :ref:`SM2_PC <SM2_PC-details-label>`, "Direct read / write access to the SM's instruction pointer / program counter."
   0x0dc, :ref:`SM2_ISR <SM2_ISR-details-label>`, "Direct read / write access to the SM's input shift register."
   0x0e0, :ref:`SM2_ISR_SHIFT_COUNT <SM2_ISR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's input shift count register."
   0x0e4, :ref:`SM2_OSR <SM2_OSR-details-label>`, "Direct read / write access to all of the SM's output shift register."
   0x0e8, :ref:`SM2_OSR_SHIFT_COUNT <SM2_OSR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's output shift count register."
   0x0ec, :ref:`SM2_FIFO_MEM0 <SM2_FIFO_MEM0-details-label>`, "Read / write access to FIFO memory word."
   0x0f0, :ref:`SM2_FIFO_MEM1 <SM2_FIFO_MEM1-details-label>`, "Read / write access to FIFO memory word."
   0x0f4, :ref:`SM2_FIFO_MEM2 <SM2_FIFO_MEM2-details-label>`, "Read / write access to FIFO memory word."
   0x0f8, :ref:`SM2_FIFO_MEM3 <SM2_FIFO_MEM3-details-label>`, "Read / write access to FIFO memory word."
   0x0fc, :ref:`SM2_FIFO_MEM4 <SM2_FIFO_MEM4-details-label>`, "Read / write access to FIFO memory word."
   0x100, :ref:`SM2_FIFO_MEM5 <SM2_FIFO_MEM5-details-label>`, "Read / write access to FIFO memory word."
   0x104, :ref:`SM2_FIFO_MEM6 <SM2_FIFO_MEM6-details-label>`, "Read / write access to FIFO memory word."
   0x108, :ref:`SM2_FIFO_MEM7 <SM2_FIFO_MEM7-details-label>`, "Read / write access to FIFO memory word."
   0x10c, :ref:`SM2_CLEAR_FORCED <SM2_CLEAR_FORCED-details-label>`, "When writing to this address, any pending forced instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x110, :ref:`SM2_CLEAR_EXECD <SM2_CLEAR_EXECD-details-label>`, "When writing to this address, any pending EXEC'd instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x114, :ref:`SM2_INSTR_ORIGIN <SM2_INSTR_ORIGIN-details-label>`, "Direct read-only access to the origin of the SM's currently executed instruction.  The mode bits determine the origin category.  If the origin category is memory address, the memory address bits will contain the memory instruction's address. Otherwise, the bits of the memory address are undefined. Note that for memory instructions, the address may differ from the value of the instruction pointer PC, if the PC has already been updated while the instruction is still in progress."
   0x118, :ref:`SM2_DELAY <SM2_DELAY-details-label>`, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x11c, :ref:`SM2_DELAY_CYCLE <SM2_DELAY_CYCLE-details-label>`, "Read-only access to the SM's delay status."
   0x120, :ref:`SM2_PENDING_DELAY <SM2_PENDING_DELAY-details-label>`, "Direct read-only access to the SM's number of pending delay cycles."
   0x124, :ref:`SM2_FORCED_INSTR <SM2_FORCED_INSTR-details-label>`, "Direct read-only access to the op-code of a forced instruction that is awaiting execution during the next clock cycle.  For writing a forced instruction, use SMx_INSTR of PIORegisters instead."
   0x128, :ref:`SM2_EXECD_INSTR <SM2_EXECD_INSTR-details-label>`, "Direct read/write access to the op-code of an EXEC'd instruction that is awaiting execution during the next clock cycle, unless the state machine's clock signal does not evaluate to true, or there is a pending forced instruction, in which case the forced instruction will be executed first."
   0x12c, :ref:`SM2_CLK_ENABLE <SM2_CLK_ENABLE-details-label>`, "Read-only access to the SM's delay status."
   0x130, :ref:`SM2_BREAKPOINTS <SM2_BREAKPOINTS-details-label>`, "Each bit of this value corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x134, :ref:`SM2_TRACEPOINTS <SM2_TRACEPOINTS-details-label>`, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is typically printed to console output (depending on the specific client application).  The message may, for example, caontain the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x138, :ref:`SM3_REGX <SM3_REGX-details-label>`, "Direct read / write access to the SM's scratch register X."
   0x13c, :ref:`SM3_REGY <SM3_REGY-details-label>`, "Direct read / write access to the SM's scratch register Y."
   0x140, :ref:`SM3_PC <SM3_PC-details-label>`, "Direct read / write access to the SM's instruction pointer / program counter."
   0x144, :ref:`SM3_ISR <SM3_ISR-details-label>`, "Direct read / write access to the SM's input shift register."
   0x148, :ref:`SM3_ISR_SHIFT_COUNT <SM3_ISR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's input shift count register."
   0x14c, :ref:`SM3_OSR <SM3_OSR-details-label>`, "Direct read / write access to all of the SM's output shift register."
   0x150, :ref:`SM3_OSR_SHIFT_COUNT <SM3_OSR_SHIFT_COUNT-details-label>`, "Direct read / write access to the SM's output shift count register."
   0x154, :ref:`SM3_FIFO_MEM0 <SM3_FIFO_MEM0-details-label>`, "Read / write access to FIFO memory word."
   0x158, :ref:`SM3_FIFO_MEM1 <SM3_FIFO_MEM1-details-label>`, "Read / write access to FIFO memory word."
   0x15c, :ref:`SM3_FIFO_MEM2 <SM3_FIFO_MEM2-details-label>`, "Read / write access to FIFO memory word."
   0x160, :ref:`SM3_FIFO_MEM3 <SM3_FIFO_MEM3-details-label>`, "Read / write access to FIFO memory word."
   0x164, :ref:`SM3_FIFO_MEM4 <SM3_FIFO_MEM4-details-label>`, "Read / write access to FIFO memory word."
   0x168, :ref:`SM3_FIFO_MEM5 <SM3_FIFO_MEM5-details-label>`, "Read / write access to FIFO memory word."
   0x16c, :ref:`SM3_FIFO_MEM6 <SM3_FIFO_MEM6-details-label>`, "Read / write access to FIFO memory word."
   0x170, :ref:`SM3_FIFO_MEM7 <SM3_FIFO_MEM7-details-label>`, "Read / write access to FIFO memory word."
   0x174, :ref:`SM3_CLEAR_FORCED <SM3_CLEAR_FORCED-details-label>`, "When writing to this address, any pending forced instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x178, :ref:`SM3_CLEAR_EXECD <SM3_CLEAR_EXECD-details-label>`, "When writing to this address, any pending EXEC'd instruction is cancelled, provided that instruction fetch & decode has not yet been started."
   0x17c, :ref:`SM3_INSTR_ORIGIN <SM3_INSTR_ORIGIN-details-label>`, "Direct read-only access to the origin of the SM's currently executed instruction.  The mode bits determine the origin category.  If the origin category is memory address, the memory address bits will contain the memory instruction's address. Otherwise, the bits of the memory address are undefined. Note that for memory instructions, the address may differ from the value of the instruction pointer PC, if the PC has already been updated while the instruction is still in progress."
   0x180, :ref:`SM3_DELAY <SM3_DELAY-details-label>`, "Direct read-only access to the SM's currently executed instruction's number of delay cycles."
   0x184, :ref:`SM3_DELAY_CYCLE <SM3_DELAY_CYCLE-details-label>`, "Read-only access to the SM's delay status."
   0x188, :ref:`SM3_PENDING_DELAY <SM3_PENDING_DELAY-details-label>`, "Direct read-only access to the SM's number of pending delay cycles."
   0x18c, :ref:`SM3_FORCED_INSTR <SM3_FORCED_INSTR-details-label>`, "Direct read-only access to the op-code of a forced instruction that is awaiting execution during the next clock cycle.  For writing a forced instruction, use SMx_INSTR of PIORegisters instead."
   0x190, :ref:`SM3_EXECD_INSTR <SM3_EXECD_INSTR-details-label>`, "Direct read/write access to the op-code of an EXEC'd instruction that is awaiting execution during the next clock cycle, unless the state machine's clock signal does not evaluate to true, or there is a pending forced instruction, in which case the forced instruction will be executed first."
   0x194, :ref:`SM3_CLK_ENABLE <SM3_CLK_ENABLE-details-label>`, "Read-only access to the SM's delay status."
   0x198, :ref:`SM3_BREAKPOINTS <SM3_BREAKPOINTS-details-label>`, "Each bit of this value corresponds to each of the 32 memory locations of the PIO instruction memory (with the LSB of the word corresponding to the lowest memory address).  Setting a bit to 1 marks the corresponding memory address as location of a breakpoint.  Setting a bit to 0 removes the breakpoint.  As soon as the program counter of the state machine reaches an address that is marked as a breakpoint, master clock MASTERCLK_MODE will be automatically set to single step mode."
   0x19c, :ref:`SM3_TRACEPOINTS <SM3_TRACEPOINTS-details-label>`, "Tracepoints work like breakpoints with the difference that master clock MASTERCLK_MODE it not automatically set to single step mode, but instead a message is typically printed to console output (depending on the specific client application).  The message may, for example, caontain the state machine's number and disassembled instruction with prefixed instruction memory address.  Tracepoints work in all master clock MASTERCLK_MODE modes."
   0x1a0, :ref:`INSTR_MEM0 <INSTR_MEM0-details-label>`, "Read / write access to instruction memory word."
   0x1a4, :ref:`INSTR_MEM1 <INSTR_MEM1-details-label>`, "Read / write access to instruction memory word."
   0x1a8, :ref:`INSTR_MEM2 <INSTR_MEM2-details-label>`, "Read / write access to instruction memory word."
   0x1ac, :ref:`INSTR_MEM3 <INSTR_MEM3-details-label>`, "Read / write access to instruction memory word."
   0x1b0, :ref:`INSTR_MEM4 <INSTR_MEM4-details-label>`, "Read / write access to instruction memory word."
   0x1b4, :ref:`INSTR_MEM5 <INSTR_MEM5-details-label>`, "Read / write access to instruction memory word."
   0x1b8, :ref:`INSTR_MEM6 <INSTR_MEM6-details-label>`, "Read / write access to instruction memory word."
   0x1bc, :ref:`INSTR_MEM7 <INSTR_MEM7-details-label>`, "Read / write access to instruction memory word."
   0x1c0, :ref:`INSTR_MEM8 <INSTR_MEM8-details-label>`, "Read / write access to instruction memory word."
   0x1c4, :ref:`INSTR_MEM9 <INSTR_MEM9-details-label>`, "Read / write access to instruction memory word."
   0x1c8, :ref:`INSTR_MEM10 <INSTR_MEM10-details-label>`, "Read / write access to instruction memory word."
   0x1cc, :ref:`INSTR_MEM11 <INSTR_MEM11-details-label>`, "Read / write access to instruction memory word."
   0x1d0, :ref:`INSTR_MEM12 <INSTR_MEM12-details-label>`, "Read / write access to instruction memory word."
   0x1d4, :ref:`INSTR_MEM13 <INSTR_MEM13-details-label>`, "Read / write access to instruction memory word."
   0x1d8, :ref:`INSTR_MEM14 <INSTR_MEM14-details-label>`, "Read / write access to instruction memory word."
   0x1dc, :ref:`INSTR_MEM15 <INSTR_MEM15-details-label>`, "Read / write access to instruction memory word."
   0x1e0, :ref:`INSTR_MEM16 <INSTR_MEM16-details-label>`, "Read / write access to instruction memory word."
   0x1e4, :ref:`INSTR_MEM17 <INSTR_MEM17-details-label>`, "Read / write access to instruction memory word."
   0x1e8, :ref:`INSTR_MEM18 <INSTR_MEM18-details-label>`, "Read / write access to instruction memory word."
   0x1ec, :ref:`INSTR_MEM19 <INSTR_MEM19-details-label>`, "Read / write access to instruction memory word."
   0x1f0, :ref:`INSTR_MEM20 <INSTR_MEM20-details-label>`, "Read / write access to instruction memory word."
   0x1f4, :ref:`INSTR_MEM21 <INSTR_MEM21-details-label>`, "Read / write access to instruction memory word."
   0x1f8, :ref:`INSTR_MEM22 <INSTR_MEM22-details-label>`, "Read / write access to instruction memory word."
   0x1fc, :ref:`INSTR_MEM23 <INSTR_MEM23-details-label>`, "Read / write access to instruction memory word."
   0x200, :ref:`INSTR_MEM24 <INSTR_MEM24-details-label>`, "Read / write access to instruction memory word."
   0x204, :ref:`INSTR_MEM25 <INSTR_MEM25-details-label>`, "Read / write access to instruction memory word."
   0x208, :ref:`INSTR_MEM26 <INSTR_MEM26-details-label>`, "Read / write access to instruction memory word."
   0x20c, :ref:`INSTR_MEM27 <INSTR_MEM27-details-label>`, "Read / write access to instruction memory word."
   0x210, :ref:`INSTR_MEM28 <INSTR_MEM28-details-label>`, "Read / write access to instruction memory word."
   0x214, :ref:`INSTR_MEM29 <INSTR_MEM29-details-label>`, "Read / write access to instruction memory word."
   0x218, :ref:`INSTR_MEM30 <INSTR_MEM30-details-label>`, "Read / write access to instruction memory word."
   0x21c, :ref:`INSTR_MEM31 <INSTR_MEM31-details-label>`, "Read / write access to instruction memory word."
   0x220, :ref:`TXF0 <TXF0-details-label>`, "Direct read access to the TX FIFO for the corresponding state machine.  Each read pops one word from the FIFO. Attempting to read from an empty FIFO has no effect on the FIFO state, and sets the sticky FDEBUG_TXUNDER error flag for this FIFO. The data returned to the system on a read from an empty FIFO is undefined."
   0x224, :ref:`TXF1 <TXF1-details-label>`, "Direct read access to the TX FIFO for the corresponding state machine.  Each read pops one word from the FIFO. Attempting to read from an empty FIFO has no effect on the FIFO state, and sets the sticky FDEBUG_TXUNDER error flag for this FIFO. The data returned to the system on a read from an empty FIFO is undefined."
   0x228, :ref:`TXF2 <TXF2-details-label>`, "Direct read access to the TX FIFO for the corresponding state machine.  Each read pops one word from the FIFO. Attempting to read from an empty FIFO has no effect on the FIFO state, and sets the sticky FDEBUG_TXUNDER error flag for this FIFO. The data returned to the system on a read from an empty FIFO is undefined."
   0x22c, :ref:`TXF3 <TXF3-details-label>`, "Direct read access to the TX FIFO for the corresponding state machine.  Each read pops one word from the FIFO. Attempting to read from an empty FIFO has no effect on the FIFO state, and sets the sticky FDEBUG_TXUNDER error flag for this FIFO. The data returned to the system on a read from an empty FIFO is undefined."
   0x230, :ref:`RXF0 <RXF0-details-label>`, "Direct write access to the RX FIFO for the corresponding state machine.  Each write pushes one word to the FIFO.  Attempting to write to a full FIFO has no effect on the FIFO state or contents, and sets the sticky FDEBUG_RXOVER error flag for this FIFO."
   0x234, :ref:`RXF1 <RXF1-details-label>`, "Direct write access to the RX FIFO for the corresponding state machine.  Each write pushes one word to the FIFO.  Attempting to write to a full FIFO has no effect on the FIFO state or contents, and sets the sticky FDEBUG_RXOVER error flag for this FIFO."
   0x238, :ref:`RXF2 <RXF2-details-label>`, "Direct write access to the RX FIFO for the corresponding state machine.  Each write pushes one word to the FIFO.  Attempting to write to a full FIFO has no effect on the FIFO state or contents, and sets the sticky FDEBUG_RXOVER error flag for this FIFO."
   0x23c, :ref:`RXF3 <RXF3-details-label>`, "Direct write access to the RX FIFO for the corresponding state machine.  Each write pushes one word to the FIFO.  Attempting to write to a full FIFO has no effect on the FIFO state or contents, and sets the sticky FDEBUG_RXOVER error flag for this FIFO."
   0x240, :ref:`FREAD_PTR <FREAD_PTR-details-label>`, "Read pointers of all of the SM's TX and RX FIFOs."
   0x244, :ref:`GPIO_PINS <GPIO_PINS-details-label>`, "Direct read / write access to all of the 32 GPIO pins."
   0x248, :ref:`GPIO_PINDIRS <GPIO_PINDIRS-details-label>`, "Direct read / write access to all of the 32 GPIO pin directions."

.. _SM0_REGX-details-label:
.. _SM1_REGX-details-label:
.. _SM2_REGX-details-label:
.. _SM3_REGX-details-label:

.. index::
   single: register details; SM0_REGX
   single: SM0_REGX

.. index::
   single: register details; SM1_REGX
   single: SM1_REGX

.. index::
   single: register details; SM2_REGX
   single: SM2_REGX

.. index::
   single: register details; SM3_REGX
   single: SM3_REGX

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_REGX, SM1_REGX, SM2_REGX, SM3_REGX Registers
--------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x000, 0x068, 0x0d0, 0x138

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's scratch register X.", RW, 0

.. _SM0_REGY-details-label:
.. _SM1_REGY-details-label:
.. _SM2_REGY-details-label:
.. _SM3_REGY-details-label:

.. index::
   single: register details; SM0_REGY
   single: SM0_REGY

.. index::
   single: register details; SM1_REGY
   single: SM1_REGY

.. index::
   single: register details; SM2_REGY
   single: SM2_REGY

.. index::
   single: register details; SM3_REGY
   single: SM3_REGY

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_REGY, SM1_REGY, SM2_REGY, SM3_REGY Registers
--------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x004, 0x06c, 0x0d4, 0x13c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's scratch register Y.", RW, 0

.. _SM0_PC-details-label:
.. _SM1_PC-details-label:
.. _SM2_PC-details-label:
.. _SM3_PC-details-label:

.. index::
   single: register details; SM0_PC
   single: SM0_PC

.. index::
   single: register details; SM1_PC
   single: SM1_PC

.. index::
   single: register details; SM2_PC
   single: SM2_PC

.. index::
   single: register details; SM3_PC
   single: SM3_PC

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_PC, SM1_PC, SM2_PC, SM3_PC Registers
------------------------------------------------------------------------------------------------------------

**Offsets:** 0x008, 0x070, 0x0d8, 0x140

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's instruction pointer / program counter.", RW, 0

.. _SM0_ISR-details-label:
.. _SM1_ISR-details-label:
.. _SM2_ISR-details-label:
.. _SM3_ISR-details-label:

.. index::
   single: register details; SM0_ISR
   single: SM0_ISR

.. index::
   single: register details; SM1_ISR
   single: SM1_ISR

.. index::
   single: register details; SM2_ISR
   single: SM2_ISR

.. index::
   single: register details; SM3_ISR
   single: SM3_ISR

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_ISR, SM1_ISR, SM2_ISR, SM3_ISR Registers
----------------------------------------------------------------------------------------------------------------

**Offsets:** 0x00c, 0x074, 0x0dc, 0x144

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's input shift register.", RW, 0

.. _SM0_ISR_SHIFT_COUNT-details-label:
.. _SM1_ISR_SHIFT_COUNT-details-label:
.. _SM2_ISR_SHIFT_COUNT-details-label:
.. _SM3_ISR_SHIFT_COUNT-details-label:

.. index::
   single: register details; SM0_ISR_SHIFT_COUNT
   single: SM0_ISR_SHIFT_COUNT

.. index::
   single: register details; SM1_ISR_SHIFT_COUNT
   single: SM1_ISR_SHIFT_COUNT

.. index::
   single: register details; SM2_ISR_SHIFT_COUNT
   single: SM2_ISR_SHIFT_COUNT

.. index::
   single: register details; SM3_ISR_SHIFT_COUNT
   single: SM3_ISR_SHIFT_COUNT

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_ISR_SHIFT_COUNT, SM1_ISR_SHIFT_COUNT, SM2_ISR_SHIFT_COUNT, SM3_ISR_SHIFT_COUNT Registers
----------------------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x010, 0x078, 0x0e0, 0x148

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's input shift count register.", RW, 0

.. _SM0_OSR-details-label:
.. _SM1_OSR-details-label:
.. _SM2_OSR-details-label:
.. _SM3_OSR-details-label:

.. index::
   single: register details; SM0_OSR
   single: SM0_OSR

.. index::
   single: register details; SM1_OSR
   single: SM1_OSR

.. index::
   single: register details; SM2_OSR
   single: SM2_OSR

.. index::
   single: register details; SM3_OSR
   single: SM3_OSR

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_OSR, SM1_OSR, SM2_OSR, SM3_OSR Registers
----------------------------------------------------------------------------------------------------------------

**Offsets:** 0x014, 0x07c, 0x0e4, 0x14c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to all of the SM's output shift register.", RW, 0

.. _SM0_OSR_SHIFT_COUNT-details-label:
.. _SM1_OSR_SHIFT_COUNT-details-label:
.. _SM2_OSR_SHIFT_COUNT-details-label:
.. _SM3_OSR_SHIFT_COUNT-details-label:

.. index::
   single: register details; SM0_OSR_SHIFT_COUNT
   single: SM0_OSR_SHIFT_COUNT

.. index::
   single: register details; SM1_OSR_SHIFT_COUNT
   single: SM1_OSR_SHIFT_COUNT

.. index::
   single: register details; SM2_OSR_SHIFT_COUNT
   single: SM2_OSR_SHIFT_COUNT

.. index::
   single: register details; SM3_OSR_SHIFT_COUNT
   single: SM3_OSR_SHIFT_COUNT

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_OSR_SHIFT_COUNT, SM1_OSR_SHIFT_COUNT, SM2_OSR_SHIFT_COUNT, SM3_OSR_SHIFT_COUNT Registers
----------------------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x018, 0x080, 0x0e8, 0x150

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read / write access to the SM's output shift count register.", RW, 0

.. _SM0_FIFO_MEM0-details-label:
.. _SM0_FIFO_MEM1-details-label:
.. _SM0_FIFO_MEM2-details-label:
.. _SM0_FIFO_MEM3-details-label:
.. _SM0_FIFO_MEM4-details-label:
.. _SM0_FIFO_MEM5-details-label:
.. _SM0_FIFO_MEM6-details-label:
.. _SM0_FIFO_MEM7-details-label:
.. _SM1_FIFO_MEM0-details-label:
.. _SM1_FIFO_MEM1-details-label:
.. _SM1_FIFO_MEM2-details-label:
.. _SM1_FIFO_MEM3-details-label:
.. _SM1_FIFO_MEM4-details-label:
.. _SM1_FIFO_MEM5-details-label:
.. _SM1_FIFO_MEM6-details-label:
.. _SM1_FIFO_MEM7-details-label:
.. _SM2_FIFO_MEM0-details-label:
.. _SM2_FIFO_MEM1-details-label:
.. _SM2_FIFO_MEM2-details-label:
.. _SM2_FIFO_MEM3-details-label:
.. _SM2_FIFO_MEM4-details-label:
.. _SM2_FIFO_MEM5-details-label:
.. _SM2_FIFO_MEM6-details-label:
.. _SM2_FIFO_MEM7-details-label:
.. _SM3_FIFO_MEM0-details-label:
.. _SM3_FIFO_MEM1-details-label:
.. _SM3_FIFO_MEM2-details-label:
.. _SM3_FIFO_MEM3-details-label:
.. _SM3_FIFO_MEM4-details-label:
.. _SM3_FIFO_MEM5-details-label:
.. _SM3_FIFO_MEM6-details-label:
.. _SM3_FIFO_MEM7-details-label:

.. index::
   single: register details; SM0_FIFO_MEM0
   single: SM0_FIFO_MEM0

.. index::
   single: register details; SM0_FIFO_MEM1
   single: SM0_FIFO_MEM1

.. index::
   single: register details; SM0_FIFO_MEM2
   single: SM0_FIFO_MEM2

.. index::
   single: register details; SM0_FIFO_MEM3
   single: SM0_FIFO_MEM3

.. index::
   single: register details; SM0_FIFO_MEM4
   single: SM0_FIFO_MEM4

.. index::
   single: register details; SM0_FIFO_MEM5
   single: SM0_FIFO_MEM5

.. index::
   single: register details; SM0_FIFO_MEM6
   single: SM0_FIFO_MEM6

.. index::
   single: register details; SM0_FIFO_MEM7
   single: SM0_FIFO_MEM7

.. index::
   single: register details; SM1_FIFO_MEM0
   single: SM1_FIFO_MEM0

.. index::
   single: register details; SM1_FIFO_MEM1
   single: SM1_FIFO_MEM1

.. index::
   single: register details; SM1_FIFO_MEM2
   single: SM1_FIFO_MEM2

.. index::
   single: register details; SM1_FIFO_MEM3
   single: SM1_FIFO_MEM3

.. index::
   single: register details; SM1_FIFO_MEM4
   single: SM1_FIFO_MEM4

.. index::
   single: register details; SM1_FIFO_MEM5
   single: SM1_FIFO_MEM5

.. index::
   single: register details; SM1_FIFO_MEM6
   single: SM1_FIFO_MEM6

.. index::
   single: register details; SM1_FIFO_MEM7
   single: SM1_FIFO_MEM7

.. index::
   single: register details; SM2_FIFO_MEM0
   single: SM2_FIFO_MEM0

.. index::
   single: register details; SM2_FIFO_MEM1
   single: SM2_FIFO_MEM1

.. index::
   single: register details; SM2_FIFO_MEM2
   single: SM2_FIFO_MEM2

.. index::
   single: register details; SM2_FIFO_MEM3
   single: SM2_FIFO_MEM3

.. index::
   single: register details; SM2_FIFO_MEM4
   single: SM2_FIFO_MEM4

.. index::
   single: register details; SM2_FIFO_MEM5
   single: SM2_FIFO_MEM5

.. index::
   single: register details; SM2_FIFO_MEM6
   single: SM2_FIFO_MEM6

.. index::
   single: register details; SM2_FIFO_MEM7
   single: SM2_FIFO_MEM7

.. index::
   single: register details; SM3_FIFO_MEM0
   single: SM3_FIFO_MEM0

.. index::
   single: register details; SM3_FIFO_MEM1
   single: SM3_FIFO_MEM1

.. index::
   single: register details; SM3_FIFO_MEM2
   single: SM3_FIFO_MEM2

.. index::
   single: register details; SM3_FIFO_MEM3
   single: SM3_FIFO_MEM3

.. index::
   single: register details; SM3_FIFO_MEM4
   single: SM3_FIFO_MEM4

.. index::
   single: register details; SM3_FIFO_MEM5
   single: SM3_FIFO_MEM5

.. index::
   single: register details; SM3_FIFO_MEM6
   single: SM3_FIFO_MEM6

.. index::
   single: register details; SM3_FIFO_MEM7
   single: SM3_FIFO_MEM7

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_FIFO_MEM0, SM0_FIFO_MEM1, SM0_FIFO_MEM2, SM0_FIFO_MEM3, SM0_FIFO_MEM4, SM0_FIFO_MEM5, SM0_FIFO_MEM6, SM0_FIFO_MEM7, SM1_FIFO_MEM0, SM1_FIFO_MEM1, SM1_FIFO_MEM2, SM1_FIFO_MEM3, SM1_FIFO_MEM4, SM1_FIFO_MEM5, SM1_FIFO_MEM6, SM1_FIFO_MEM7, SM2_FIFO_MEM0, SM2_FIFO_MEM1, SM2_FIFO_MEM2, SM2_FIFO_MEM3, SM2_FIFO_MEM4, SM2_FIFO_MEM5, SM2_FIFO_MEM6, SM2_FIFO_MEM7, SM3_FIFO_MEM0, SM3_FIFO_MEM1, SM3_FIFO_MEM2, SM3_FIFO_MEM3, SM3_FIFO_MEM4, SM3_FIFO_MEM5, SM3_FIFO_MEM6, SM3_FIFO_MEM7 Registers
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x01c, 0x020, 0x024, 0x028, 0x02c, 0x030, 0x034, 0x038, 0x084, 0x088, 0x08c, 0x090, 0x094, 0x098, 0x09c, 0x0a0, 0x0ec, 0x0f0, 0x0f4, 0x0f8, 0x0fc, 0x100, 0x104, 0x108, 0x154, 0x158, 0x15c, 0x160, 0x164, 0x168, 0x16c, 0x170

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Read / write access to FIFO memory word.", RW, 0

.. _SM0_CLEAR_FORCED-details-label:
.. _SM1_CLEAR_FORCED-details-label:
.. _SM2_CLEAR_FORCED-details-label:
.. _SM3_CLEAR_FORCED-details-label:

.. index::
   single: register details; SM0_CLEAR_FORCED
   single: SM0_CLEAR_FORCED

.. index::
   single: register details; SM1_CLEAR_FORCED
   single: SM1_CLEAR_FORCED

.. index::
   single: register details; SM2_CLEAR_FORCED
   single: SM2_CLEAR_FORCED

.. index::
   single: register details; SM3_CLEAR_FORCED
   single: SM3_CLEAR_FORCED

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_CLEAR_FORCED, SM1_CLEAR_FORCED, SM2_CLEAR_FORCED, SM3_CLEAR_FORCED Registers
----------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x03c, 0x0a4, 0x10c, 0x174

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "When writing to this address, any pending forced instruction is cancelled, provided that instruction fetch & decode has not yet been started.", WF, 0

.. _SM0_CLEAR_EXECD-details-label:
.. _SM1_CLEAR_EXECD-details-label:
.. _SM2_CLEAR_EXECD-details-label:
.. _SM3_CLEAR_EXECD-details-label:

.. index::
   single: register details; SM0_CLEAR_EXECD
   single: SM0_CLEAR_EXECD

.. index::
   single: register details; SM1_CLEAR_EXECD
   single: SM1_CLEAR_EXECD

.. index::
   single: register details; SM2_CLEAR_EXECD
   single: SM2_CLEAR_EXECD

.. index::
   single: register details; SM3_CLEAR_EXECD
   single: SM3_CLEAR_EXECD

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_CLEAR_EXECD, SM1_CLEAR_EXECD, SM2_CLEAR_EXECD, SM3_CLEAR_EXECD Registers
------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x040, 0x0a8, 0x110, 0x178

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "When writing to this address, any pending EXEC'd instruction is cancelled, provided that instruction fetch & decode has not yet been started.", WF, 0

.. _SM0_INSTR_ORIGIN-details-label:
.. _SM1_INSTR_ORIGIN-details-label:
.. _SM2_INSTR_ORIGIN-details-label:
.. _SM3_INSTR_ORIGIN-details-label:

.. index::
   single: register details; SM0_INSTR_ORIGIN
   single: SM0_INSTR_ORIGIN

.. index::
   single: register details; SM1_INSTR_ORIGIN
   single: SM1_INSTR_ORIGIN

.. index::
   single: register details; SM2_INSTR_ORIGIN
   single: SM2_INSTR_ORIGIN

.. index::
   single: register details; SM3_INSTR_ORIGIN
   single: SM3_INSTR_ORIGIN

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_INSTR_ORIGIN, SM1_INSTR_ORIGIN, SM2_INSTR_ORIGIN, SM3_INSTR_ORIGIN Registers
----------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x044, 0x0ac, 0x114, 0x17c

**Description**

Direct read-only access to the origin of the SM's
currently executed instruction.  The mode bits
determine the origin category.  If the origin
category is memory address, the memory address bits
will contain the memory instruction's address.
Otherwise, the bits of the memory address are
undefined.
Note that for memory instructions, the address may
differ from the value of the instruction pointer PC,
if the PC has already been updated while the
instruction is still in progress.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:7, Reserved., "―", ―, ―
   6:5, CATEGORY, "For forced instructions, this is the value 3. For EXEC'd instructions, this is the value 2. Otherwise (e.g. after reset), this is the value 1. ", RO, 1
   4:0, MEMORY_ADDRESS, "memory address value (0x00…0x1f)", RO, 0

.. _SM0_DELAY-details-label:
.. _SM1_DELAY-details-label:
.. _SM2_DELAY-details-label:
.. _SM3_DELAY-details-label:

.. index::
   single: register details; SM0_DELAY
   single: SM0_DELAY

.. index::
   single: register details; SM1_DELAY
   single: SM1_DELAY

.. index::
   single: register details; SM2_DELAY
   single: SM2_DELAY

.. index::
   single: register details; SM3_DELAY
   single: SM3_DELAY

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_DELAY, SM1_DELAY, SM2_DELAY, SM3_DELAY Registers
------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x048, 0x0b0, 0x118, 0x180

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:5, Reserved., "―", ―, ―
   4:0, ―, "Direct read-only access to the SM's currently executed instruction's number of delay cycles.", RO, 0

.. _SM0_DELAY_CYCLE-details-label:
.. _SM1_DELAY_CYCLE-details-label:
.. _SM2_DELAY_CYCLE-details-label:
.. _SM3_DELAY_CYCLE-details-label:

.. index::
   single: register details; SM0_DELAY_CYCLE
   single: SM0_DELAY_CYCLE

.. index::
   single: register details; SM1_DELAY_CYCLE
   single: SM1_DELAY_CYCLE

.. index::
   single: register details; SM2_DELAY_CYCLE
   single: SM2_DELAY_CYCLE

.. index::
   single: register details; SM3_DELAY_CYCLE
   single: SM3_DELAY_CYCLE

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_DELAY_CYCLE, SM1_DELAY_CYCLE, SM2_DELAY_CYCLE, SM3_DELAY_CYCLE Registers
------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x04c, 0x0b4, 0x11c, 0x184

**Description**

Read-only access to the SM's delay status.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:1, Reserved., "―", ―, ―
   0, DELAY_CYCLE, "0x1, if the currently executed cycles is a delay cycle.", RO, 0

.. _SM0_PENDING_DELAY-details-label:
.. _SM1_PENDING_DELAY-details-label:
.. _SM2_PENDING_DELAY-details-label:
.. _SM3_PENDING_DELAY-details-label:

.. index::
   single: register details; SM0_PENDING_DELAY
   single: SM0_PENDING_DELAY

.. index::
   single: register details; SM1_PENDING_DELAY
   single: SM1_PENDING_DELAY

.. index::
   single: register details; SM2_PENDING_DELAY
   single: SM2_PENDING_DELAY

.. index::
   single: register details; SM3_PENDING_DELAY
   single: SM3_PENDING_DELAY

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_PENDING_DELAY, SM1_PENDING_DELAY, SM2_PENDING_DELAY, SM3_PENDING_DELAY Registers
--------------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x050, 0x0b8, 0x120, 0x188

**Description**

Direct read-only access to the SM's
number of pending delay cycles.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:5, Reserved., "―", ―, ―
   4:0, PENDING_DELAY, "Number (0x00…0x1f) of pending delays of the currently executed instruction.", RO, 0

.. _SM0_FORCED_INSTR-details-label:
.. _SM1_FORCED_INSTR-details-label:
.. _SM2_FORCED_INSTR-details-label:
.. _SM3_FORCED_INSTR-details-label:

.. index::
   single: register details; SM0_FORCED_INSTR
   single: SM0_FORCED_INSTR

.. index::
   single: register details; SM1_FORCED_INSTR
   single: SM1_FORCED_INSTR

.. index::
   single: register details; SM2_FORCED_INSTR
   single: SM2_FORCED_INSTR

.. index::
   single: register details; SM3_FORCED_INSTR
   single: SM3_FORCED_INSTR

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_FORCED_INSTR, SM1_FORCED_INSTR, SM2_FORCED_INSTR, SM3_FORCED_INSTR Registers
----------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x054, 0x0bc, 0x124, 0x18c

**Description**

Direct read-only access to the op-code of a forced
instruction that is awaiting execution during the
next clock cycle.  For writing a forced instruction,
use SMx_INSTR of PIORegisters instead.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:17, Reserved., "―", ―, ―
   16, PENDING, "0x1, if a forced instruction is awaiting execution, otherwise 0x0.", RO, 0
   15:0, INSTR, "Instruction op-code, if any; otherwise, 0x0000.", RO, 0

.. _SM0_EXECD_INSTR-details-label:
.. _SM1_EXECD_INSTR-details-label:
.. _SM2_EXECD_INSTR-details-label:
.. _SM3_EXECD_INSTR-details-label:

.. index::
   single: register details; SM0_EXECD_INSTR
   single: SM0_EXECD_INSTR

.. index::
   single: register details; SM1_EXECD_INSTR
   single: SM1_EXECD_INSTR

.. index::
   single: register details; SM2_EXECD_INSTR
   single: SM2_EXECD_INSTR

.. index::
   single: register details; SM3_EXECD_INSTR
   single: SM3_EXECD_INSTR

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_EXECD_INSTR, SM1_EXECD_INSTR, SM2_EXECD_INSTR, SM3_EXECD_INSTR Registers
------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x058, 0x0c0, 0x128, 0x190

**Description**

Direct read/write access to the op-code of an EXEC'd
instruction that is awaiting execution during the
next clock cycle, unless the state machine's clock
signal does not evaluate to true, or there is a
pending forced instruction, in which case the forced
instruction will be executed first.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:17, Reserved., "―", ―, ―
   16, PENDING, "0x1, if an EXEC'd instruction is awaiting execution, otherwise 0x0.", RO, 0
   15:0, INSTR, "Instruction op-code, if any; otherwise, 0x0000.", RW, 0

.. _SM0_CLK_ENABLE-details-label:
.. _SM1_CLK_ENABLE-details-label:
.. _SM2_CLK_ENABLE-details-label:
.. _SM3_CLK_ENABLE-details-label:

.. index::
   single: register details; SM0_CLK_ENABLE
   single: SM0_CLK_ENABLE

.. index::
   single: register details; SM1_CLK_ENABLE
   single: SM1_CLK_ENABLE

.. index::
   single: register details; SM2_CLK_ENABLE
   single: SM2_CLK_ENABLE

.. index::
   single: register details; SM3_CLK_ENABLE
   single: SM3_CLK_ENABLE

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_CLK_ENABLE, SM1_CLK_ENABLE, SM2_CLK_ENABLE, SM3_CLK_ENABLE Registers
--------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x05c, 0x0c4, 0x12c, 0x194

**Description**

Read-only access to the SM's delay status.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:1, Reserved., "―", ―, ―
   0, DELAY_CYCLE, "0x1, if in the current cycle the clock enable signal evaluates to 0x1.", RO, 0

.. _SM0_BREAKPOINTS-details-label:
.. _SM1_BREAKPOINTS-details-label:
.. _SM2_BREAKPOINTS-details-label:
.. _SM3_BREAKPOINTS-details-label:

.. index::
   single: register details; SM0_BREAKPOINTS
   single: SM0_BREAKPOINTS

.. index::
   single: register details; SM1_BREAKPOINTS
   single: SM1_BREAKPOINTS

.. index::
   single: register details; SM2_BREAKPOINTS
   single: SM2_BREAKPOINTS

.. index::
   single: register details; SM3_BREAKPOINTS
   single: SM3_BREAKPOINTS

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_BREAKPOINTS, SM1_BREAKPOINTS, SM2_BREAKPOINTS, SM3_BREAKPOINTS Registers
------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x060, 0x0c8, 0x130, 0x198

**Description**

Each bit of this value corresponds to each of the
32 memory locations of the PIO instruction memory
(with the LSB of the word corresponding to the lowest
memory address).  Setting a bit to 1 marks the
corresponding memory address as location of a
breakpoint.  Setting a bit to 0 removes the
breakpoint.

As soon as the program counter of the state machine
reaches an address that is marked as a breakpoint,
master clock MASTERCLK_MODE will be automatically set
to single step mode.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, BP_MEM31, "0x1, if the memory address is marked as breakpoint.", RW, 0
   30, BP_MEM30, "0x1, if the memory address is marked as breakpoint.", RW, 0
   29, BP_MEM29, "0x1, if the memory address is marked as breakpoint.", RW, 0
   28, BP_MEM28, "0x1, if the memory address is marked as breakpoint.", RW, 0
   27, BP_MEM27, "0x1, if the memory address is marked as breakpoint.", RW, 0
   26, BP_MEM26, "0x1, if the memory address is marked as breakpoint.", RW, 0
   25, BP_MEM25, "0x1, if the memory address is marked as breakpoint.", RW, 0
   24, BP_MEM24, "0x1, if the memory address is marked as breakpoint.", RW, 0
   23, BP_MEM23, "0x1, if the memory address is marked as breakpoint.", RW, 0
   22, BP_MEM22, "0x1, if the memory address is marked as breakpoint.", RW, 0
   21, BP_MEM21, "0x1, if the memory address is marked as breakpoint.", RW, 0
   20, BP_MEM20, "0x1, if the memory address is marked as breakpoint.", RW, 0
   19, BP_MEM19, "0x1, if the memory address is marked as breakpoint.", RW, 0
   18, BP_MEM18, "0x1, if the memory address is marked as breakpoint.", RW, 0
   17, BP_MEM17, "0x1, if the memory address is marked as breakpoint.", RW, 0
   16, BP_MEM16, "0x1, if the memory address is marked as breakpoint.", RW, 0
   15, BP_MEM15, "0x1, if the memory address is marked as breakpoint.", RW, 0
   14, BP_MEM14, "0x1, if the memory address is marked as breakpoint.", RW, 0
   13, BP_MEM13, "0x1, if the memory address is marked as breakpoint.", RW, 0
   12, BP_MEM12, "0x1, if the memory address is marked as breakpoint.", RW, 0
   11, BP_MEM11, "0x1, if the memory address is marked as breakpoint.", RW, 0
   10, BP_MEM10, "0x1, if the memory address is marked as breakpoint.", RW, 0
   9, BP_MEM9, "0x1, if the memory address is marked as breakpoint.", RW, 0
   8, BP_MEM8, "0x1, if the memory address is marked as breakpoint.", RW, 0
   7, BP_MEM7, "0x1, if the memory address is marked as breakpoint.", RW, 0
   6, BP_MEM6, "0x1, if the memory address is marked as breakpoint.", RW, 0
   5, BP_MEM5, "0x1, if the memory address is marked as breakpoint.", RW, 0
   4, BP_MEM4, "0x1, if the memory address is marked as breakpoint.", RW, 0
   3, BP_MEM3, "0x1, if the memory address is marked as breakpoint.", RW, 0
   2, BP_MEM2, "0x1, if the memory address is marked as breakpoint.", RW, 0
   1, BP_MEM1, "0x1, if the memory address is marked as breakpoint.", RW, 0
   0, BP_MEM0, "0x1, if the memory address is marked as breakpoint.", RW, 0

.. _SM0_TRACEPOINTS-details-label:
.. _SM1_TRACEPOINTS-details-label:
.. _SM2_TRACEPOINTS-details-label:
.. _SM3_TRACEPOINTS-details-label:

.. index::
   single: register details; SM0_TRACEPOINTS
   single: SM0_TRACEPOINTS

.. index::
   single: register details; SM1_TRACEPOINTS
   single: SM1_TRACEPOINTS

.. index::
   single: register details; SM2_TRACEPOINTS
   single: SM2_TRACEPOINTS

.. index::
   single: register details; SM3_TRACEPOINTS
   single: SM3_TRACEPOINTS

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: SM0_TRACEPOINTS, SM1_TRACEPOINTS, SM2_TRACEPOINTS, SM3_TRACEPOINTS Registers
------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x064, 0x0cc, 0x134, 0x19c

**Description**

Tracepoints work like breakpoints with the difference
that master clock MASTERCLK_MODE it not automatically
set to single step mode, but instead a message is
typically printed to console output (depending on
the specific client application).  The message may,
for example, caontain the state machine's number and
disassembled instruction with prefixed instruction
memory address.  Tracepoints work in all master clock
MASTERCLK_MODE modes.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, TP_MEM31, "0x1, if the memory address is marked as tracepoint.", RW, 0
   30, TP_MEM30, "0x1, if the memory address is marked as tracepoint.", RW, 0
   29, TP_MEM29, "0x1, if the memory address is marked as tracepoint.", RW, 0
   28, TP_MEM28, "0x1, if the memory address is marked as tracepoint.", RW, 0
   27, TP_MEM27, "0x1, if the memory address is marked as tracepoint.", RW, 0
   26, TP_MEM26, "0x1, if the memory address is marked as tracepoint.", RW, 0
   25, TP_MEM25, "0x1, if the memory address is marked as tracepoint.", RW, 0
   24, TP_MEM24, "0x1, if the memory address is marked as tracepoint.", RW, 0
   23, TP_MEM23, "0x1, if the memory address is marked as tracepoint.", RW, 0
   22, TP_MEM22, "0x1, if the memory address is marked as tracepoint.", RW, 0
   21, TP_MEM21, "0x1, if the memory address is marked as tracepoint.", RW, 0
   20, TP_MEM20, "0x1, if the memory address is marked as tracepoint.", RW, 0
   19, TP_MEM19, "0x1, if the memory address is marked as tracepoint.", RW, 0
   18, TP_MEM18, "0x1, if the memory address is marked as tracepoint.", RW, 0
   17, TP_MEM17, "0x1, if the memory address is marked as tracepoint.", RW, 0
   16, TP_MEM16, "0x1, if the memory address is marked as tracepoint.", RW, 0
   15, TP_MEM15, "0x1, if the memory address is marked as tracepoint.", RW, 0
   14, TP_MEM14, "0x1, if the memory address is marked as tracepoint.", RW, 0
   13, TP_MEM13, "0x1, if the memory address is marked as tracepoint.", RW, 0
   12, TP_MEM12, "0x1, if the memory address is marked as tracepoint.", RW, 0
   11, TP_MEM11, "0x1, if the memory address is marked as tracepoint.", RW, 0
   10, TP_MEM10, "0x1, if the memory address is marked as tracepoint.", RW, 0
   9, TP_MEM9, "0x1, if the memory address is marked as tracepoint.", RW, 0
   8, TP_MEM8, "0x1, if the memory address is marked as tracepoint.", RW, 0
   7, TP_MEM7, "0x1, if the memory address is marked as tracepoint.", RW, 0
   6, TP_MEM6, "0x1, if the memory address is marked as tracepoint.", RW, 0
   5, TP_MEM5, "0x1, if the memory address is marked as tracepoint.", RW, 0
   4, TP_MEM4, "0x1, if the memory address is marked as tracepoint.", RW, 0
   3, TP_MEM3, "0x1, if the memory address is marked as tracepoint.", RW, 0
   2, TP_MEM2, "0x1, if the memory address is marked as tracepoint.", RW, 0
   1, TP_MEM1, "0x1, if the memory address is marked as tracepoint.", RW, 0
   0, TP_MEM0, "0x1, if the memory address is marked as tracepoint.", RW, 0

.. _INSTR_MEM0-details-label:
.. _INSTR_MEM1-details-label:
.. _INSTR_MEM2-details-label:
.. _INSTR_MEM3-details-label:
.. _INSTR_MEM4-details-label:
.. _INSTR_MEM5-details-label:
.. _INSTR_MEM6-details-label:
.. _INSTR_MEM7-details-label:
.. _INSTR_MEM8-details-label:
.. _INSTR_MEM9-details-label:
.. _INSTR_MEM10-details-label:
.. _INSTR_MEM11-details-label:
.. _INSTR_MEM12-details-label:
.. _INSTR_MEM13-details-label:
.. _INSTR_MEM14-details-label:
.. _INSTR_MEM15-details-label:
.. _INSTR_MEM16-details-label:
.. _INSTR_MEM17-details-label:
.. _INSTR_MEM18-details-label:
.. _INSTR_MEM19-details-label:
.. _INSTR_MEM20-details-label:
.. _INSTR_MEM21-details-label:
.. _INSTR_MEM22-details-label:
.. _INSTR_MEM23-details-label:
.. _INSTR_MEM24-details-label:
.. _INSTR_MEM25-details-label:
.. _INSTR_MEM26-details-label:
.. _INSTR_MEM27-details-label:
.. _INSTR_MEM28-details-label:
.. _INSTR_MEM29-details-label:
.. _INSTR_MEM30-details-label:
.. _INSTR_MEM31-details-label:

.. index::
   single: register details; INSTR_MEM0
   single: INSTR_MEM0

.. index::
   single: register details; INSTR_MEM1
   single: INSTR_MEM1

.. index::
   single: register details; INSTR_MEM2
   single: INSTR_MEM2

.. index::
   single: register details; INSTR_MEM3
   single: INSTR_MEM3

.. index::
   single: register details; INSTR_MEM4
   single: INSTR_MEM4

.. index::
   single: register details; INSTR_MEM5
   single: INSTR_MEM5

.. index::
   single: register details; INSTR_MEM6
   single: INSTR_MEM6

.. index::
   single: register details; INSTR_MEM7
   single: INSTR_MEM7

.. index::
   single: register details; INSTR_MEM8
   single: INSTR_MEM8

.. index::
   single: register details; INSTR_MEM9
   single: INSTR_MEM9

.. index::
   single: register details; INSTR_MEM10
   single: INSTR_MEM10

.. index::
   single: register details; INSTR_MEM11
   single: INSTR_MEM11

.. index::
   single: register details; INSTR_MEM12
   single: INSTR_MEM12

.. index::
   single: register details; INSTR_MEM13
   single: INSTR_MEM13

.. index::
   single: register details; INSTR_MEM14
   single: INSTR_MEM14

.. index::
   single: register details; INSTR_MEM15
   single: INSTR_MEM15

.. index::
   single: register details; INSTR_MEM16
   single: INSTR_MEM16

.. index::
   single: register details; INSTR_MEM17
   single: INSTR_MEM17

.. index::
   single: register details; INSTR_MEM18
   single: INSTR_MEM18

.. index::
   single: register details; INSTR_MEM19
   single: INSTR_MEM19

.. index::
   single: register details; INSTR_MEM20
   single: INSTR_MEM20

.. index::
   single: register details; INSTR_MEM21
   single: INSTR_MEM21

.. index::
   single: register details; INSTR_MEM22
   single: INSTR_MEM22

.. index::
   single: register details; INSTR_MEM23
   single: INSTR_MEM23

.. index::
   single: register details; INSTR_MEM24
   single: INSTR_MEM24

.. index::
   single: register details; INSTR_MEM25
   single: INSTR_MEM25

.. index::
   single: register details; INSTR_MEM26
   single: INSTR_MEM26

.. index::
   single: register details; INSTR_MEM27
   single: INSTR_MEM27

.. index::
   single: register details; INSTR_MEM28
   single: INSTR_MEM28

.. index::
   single: register details; INSTR_MEM29
   single: INSTR_MEM29

.. index::
   single: register details; INSTR_MEM30
   single: INSTR_MEM30

.. index::
   single: register details; INSTR_MEM31
   single: INSTR_MEM31

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: INSTR_MEM0, INSTR_MEM1, INSTR_MEM2, INSTR_MEM3, INSTR_MEM4, INSTR_MEM5, INSTR_MEM6, INSTR_MEM7, INSTR_MEM8, INSTR_MEM9, INSTR_MEM10, INSTR_MEM11, INSTR_MEM12, INSTR_MEM13, INSTR_MEM14, INSTR_MEM15, INSTR_MEM16, INSTR_MEM17, INSTR_MEM18, INSTR_MEM19, INSTR_MEM20, INSTR_MEM21, INSTR_MEM22, INSTR_MEM23, INSTR_MEM24, INSTR_MEM25, INSTR_MEM26, INSTR_MEM27, INSTR_MEM28, INSTR_MEM29, INSTR_MEM30, INSTR_MEM31 Registers
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Offsets:** 0x1a0, 0x1a4, 0x1a8, 0x1ac, 0x1b0, 0x1b4, 0x1b8, 0x1bc, 0x1c0, 0x1c4, 0x1c8, 0x1cc, 0x1d0, 0x1d4, 0x1d8, 0x1dc, 0x1e0, 0x1e4, 0x1e8, 0x1ec, 0x1f0, 0x1f4, 0x1f8, 0x1fc, 0x200, 0x204, 0x208, 0x20c, 0x210, 0x214, 0x218, 0x21c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Read / write access to instruction memory word.", RW, 0

.. _TXF0-details-label:
.. _TXF1-details-label:
.. _TXF2-details-label:
.. _TXF3-details-label:

.. index::
   single: register details; TXF0
   single: TXF0

.. index::
   single: register details; TXF1
   single: TXF1

.. index::
   single: register details; TXF2
   single: TXF2

.. index::
   single: register details; TXF3
   single: TXF3

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: TXF0, TXF1, TXF2, TXF3 Registers
----------------------------------------------------------------------------------------------------

**Offsets:** 0x220, 0x224, 0x228, 0x22c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct read access to the TX FIFO for the corresponding state machine.  Each read pops one word from the FIFO. Attempting to read from an empty FIFO has no effect on the FIFO state, and sets the sticky FDEBUG_TXUNDER error flag for this FIFO. The data returned to the system on a read from an empty FIFO is undefined.", RF, ―

.. _RXF0-details-label:
.. _RXF1-details-label:
.. _RXF2-details-label:
.. _RXF3-details-label:

.. index::
   single: register details; RXF0
   single: RXF0

.. index::
   single: register details; RXF1
   single: RXF1

.. index::
   single: register details; RXF2
   single: RXF2

.. index::
   single: register details; RXF3
   single: RXF3

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: RXF0, RXF1, RXF2, RXF3 Registers
----------------------------------------------------------------------------------------------------

**Offsets:** 0x230, 0x234, 0x238, 0x23c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Direct write access to the RX FIFO for the corresponding state machine.  Each write pushes one word to the FIFO.  Attempting to write to a full FIFO has no effect on the FIFO state or contents, and sets the sticky FDEBUG_RXOVER error flag for this FIFO.", WF, 0

.. _FREAD_PTR-details-label:

.. index::
   single: register details; FREAD_PTR
   single: FREAD_PTR

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: FREAD_PTR Register
--------------------------------------------------------------------------------------

**Offset:** 0x240

**Description**

Read pointers of all of the SM's TX and RX FIFOs.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:28, TXF0_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   27:24, RXF0_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   23:20, TXF1_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   19:16, RXF1_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   15:12, TXF2_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   11:8, RXF2_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   7:4, TXF3_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0
   3:0, RXF3_READ_PTR, "Offset (0…7) within FIFO memory for the next FIFO read operation", RO, 0

.. _GPIO_PINS-details-label:

.. index::
   single: register details; GPIO_PINS
   single: GPIO_PINS

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: GPIO_PINS Register
--------------------------------------------------------------------------------------

**Offset:** 0x244

**Description**

Direct read / write access to all of the 32 GPIO pins.

.. csv-table::
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

.. _GPIO_PINDIRS-details-label:

.. index::
   single: register details; GPIO_PINDIRS
   single: GPIO_PINDIRS

:ref:`Emulator PIO Registers <section-top_emulator_pio_registers>`: GPIO_PINDIRS Register
-----------------------------------------------------------------------------------------

**Offset:** 0x248

**Description**

Direct read / write access to all of the 32 GPIO pin
directions.

.. csv-table::
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

