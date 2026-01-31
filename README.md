# 6T-SRAM-Operations
Design and simulation of a CMOS-based 6T SRAM cell focusing on Read, Write, and Hold operations along with peripheral circuits using LTSpice.

# 📌Overview
Static Random Access Memory (SRAM) is a high-speed, volatile memory technology used in digital systems to store frequently accessed data and instructions close to the processor. Unlike Dynamic Random Access Memory (DRAM), which stores data as charge on capacitors and requires periodic refresh cycles, SRAM stores information using a bistable latch formed by cross-coupled CMOS inverters. This latch-based structure allows SRAM to retain its stored value as long as power is applied, without the need for refresh operations, resulting in significantly lower access latency and simpler control logic. <br>
<br>
SRAM is widely preferred in performance-critical applications such as CPU cache memory, register files, and embedded systems due to its fast read and write capability, strong noise immunity, and stable data retention. Although SRAM occupies more silicon area and is more expensive per bit compared to DRAM, its superior speed and reliability make it the memory of choice where system performance and real-time operation are more important than storage density and cost. <br>

# 6T SRAM Cell Structure
The conventional 6-transistor (6T) SRAM cell consists of six MOSFETs arranged to form a stable and high-speed memory storage element. It is based on a bistable latch configuration created using two cross-coupled CMOS inverters, which allows the cell to store one bit of data as long as power is supplied. <br>
![Conventional 6T SRAM Cell Structure](Schematics/Conventional-6T-SRAM-cell.png)
**Transistor Composition**<br>
The six transistors are divided into three functional groups: <br>
**1. Storage Inverters (M1, M2, M3, M4)** <br>
These four transistors form two cross-coupled CMOS inverters: <br>
- M3 and M4 (PMOS Pull-Up Transistors) <br>
 Connected to VDD, they pull the internal storage nodes high when required. <br>
 
- M1 and M2 (NMOS Pull-Down Transistors) <br>
 Connected to ground, they pull the storage nodes low. <br>
 These inverters create two complementary internal nodes: <br>
 
 - Q → Stores the actual data bit <br>
 - Q̅ (Q-bar) → Stores the inverted value <br>
 This feedback structure ensures data retention and stability during the hold state. <br>
 **2. Access Transistors (M5 and M6)** <br>
 These NMOS transistors connect the internal nodes Q and Q̅ to the bit lines: <br>
 
  - BL (Bit Line) <br>
  - BLB (Bit Line Bar / Complement) <br>
- They are controlled by the Word Line (WL) <br>
**Operation:** <br>

- WL = HIGH → M5 and M6 turn ON <br>
The cell is connected to the bit lines for read or write operation <br>

- WL = LOW → M5 and M6 turn OFF <br>
The cell is isolated and remains in hold mode <br>
