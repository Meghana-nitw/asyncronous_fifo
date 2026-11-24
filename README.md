# asyncronous_fifo
# Asynchronous FIFO Design and RTL-to-GDSII Implementation

## Project Overview

This project implements an **Asynchronous First-In, First-Out (FIFO)** using Verilog HDL and completes the RTL-to-GDSII physical design flow using Synopsys tools and the SAED 32nm RVT standard-cell library.

An asynchronous FIFO enables reliable data transfer between two independent clock domains. The design uses Gray-coded read and write pointers, along with two-stage synchronizers, to safely transfer pointer information across clock domains.

## Design Specifications

| Parameter | Value |
|---|---|
| Top Module | `fifo1` |
| FIFO Type | Asynchronous Dual-Clock FIFO |
| Data Width | 8 bits |
| Address Width | 4 bits |
| FIFO Depth | 16 words |
| Storage Capacity | 128 bits |
| Write Clock | `wclk` – 10 ns period |
| Read Clock | `rclk` – 15 ns period |
| Write Reset | `wrst_n` – Active Low |
| Read Reset | `rrst_n` – Active Low |
| Status Flags | `wfull`, `rempty` |
| Technology Library | SAED 32nm RVT |

## Architecture

The top-level module `fifo1` integrates the following submodules:

- **fifomem:** Dual-port memory used for independent read and write operations.
- **sync_r2w:** Two-stage synchronizer that transfers the read pointer into the write clock domain.
- **sync_w2r:** Two-stage synchronizer that transfers the write pointer into the read clock domain.
- **wptr_full:** Write-pointer logic that generates the write pointer and FIFO full flag.
- **rptr_empty:** Read-pointer logic that generates the read pointer and FIFO empty flag.

### Key Design Concepts

- Independent read and write clock domains.
- Binary-to-Gray code pointer conversion.
- Two-stage flip-flop synchronization.
- FIFO full and empty detection.
- Dual-port memory architecture.
- Clock-domain crossing (CDC) handling.

## Tools and Technologies

- Verilog HDL – RTL design and testbench development.
- Synopsys VCS – RTL compilation and functional simulation.
- Verdi / FSDB – Waveform analysis and debugging.
- Synopsys Design Compiler – Logic synthesis and technology mapping.
- Synopsys IC Compiler II (ICC2) – Physical design and routing.
- SAED 32nm RVT – Standard-cell technology library.
- SDC – Clock and timing constraints.

## Implementation Flow

1. RTL Design – Developed the asynchronous FIFO and its submodules using Verilog HDL.
2. Functional Simulation – Simulated the design using Synopsys VCS.
3. Waveform Verification – Examined signal transitions and FIFO operations using Verdi/FSDB.
4. Logic Synthesis – Synthesized the RTL using Synopsys Design Compiler.
5. Physical Design – Performed floorplanning, placement, clock-tree synthesis and routing using ICC2.
6. Physical Verification – Evaluated timing, DRC and LVS results.

## Results

### Synthesis Results – Design Compiler

| Parameter | Result |
|---|---:|
| Cell Area | 1948.013792 |
| Dynamic Power | 105.0751 µW |
| Leakage Power | 122.5161 µW |
| Cell Count | 490 |

### Final Physical Design Results – ICC2

| Parameter | Result |
|---|---:|
| Final Cell Area | 2805.24 |
| Leaf Cells | 686 |
| Setup Violations | 0 |
| Hold Violations | 0 |
| DRC Violations | 0 |
| LVS | Clean |

*Note: Synthesis and final physical-design area values correspond to different implementation stages.*

## Key Outcomes

- Successfully designed and simulated an 8-bit asynchronous FIFO with a depth of 16 words.
- Implemented Gray-code pointer synchronization for clock-domain crossing.
- Verified FIFO write, read, full and empty operations.
- Completed synthesis and physical implementation using Synopsys tools.
- Achieved zero final setup and hold violations and clean DRC/LVS verification.

## Repository Contents

The repository contains the Verilog RTL source files, testbench, simulation files, synthesis and physical-design-related files, and supporting project documentation.

## Author

**Meghana Poduri**  
B.Tech – Electronics and Communication Engineering (VLSI-DT)  
National Institute of Technology Warangal

## Note

The SAED 32nm technology library and other licensed proprietary EDA files are not included in this repository. They must be obtained through their authorized sources.
