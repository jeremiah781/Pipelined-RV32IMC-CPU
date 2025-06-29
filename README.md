# Pipelined RV32IMC CPU 

<!-- ──────────────────────────────────  HEADER  ────────────────────────────────── -->

<div align="center">

<img src="https://img.shields.io/badge/Frequency-100.15%20MHz-FF6B35?style=for-the-badge&logo=riscv&logoColor=white" />
<img src="https://img.shields.io/badge/Area-21%25%20Smaller-4CAF50?style=for-the-badge&logo=microchip&logoColor=white" />
<img src="https://img.shields.io/badge/Timing-32%25%20Faster-9C27B0?style=for-the-badge&logo=timer&logoColor=white" />

<br><br>

<img src="https://img.shields.io/badge/FPGA-Altera%20DE1%E2%80%93SoC-0071C5?logo=intel&logoColor=white" />
<img src="https://img.shields.io/badge/Core-RV32IMC--32%20bit-brightgreen?logo=riscv&logoColor=white" />
<img src="https://img.shields.io/badge/Status-Production%20Ready-00C851?logoColor=white" />

</div>

<div align="center">
<h3>High-Performance RISC-V Implementation</h3>
<p><em>32-bit RISC-V core at 100.15 MHz</em></p>
</div>

> **Result:** A custom 32-bit RISC-V processor that **runs at 100.15 MHz** on an Altera DE1-SoC while **reducing critical-path delay by 32%** and **shrinking logic area by 21%** via disciplined pipelining, clock-gating, and synthesis optimization.

---

## Mission: First-Principles Hardware Design

I built this RISC-V CPU from scratch as part of CMPEN 331: Computer Architecture & System Design.  
What started as a class project turned into real hardware. I got it running on the DE1-SoC board, fully functional and pipelined.

**Philosophy:** *Clean RTL + Systematic Optimization + Data-Driven Decisions = Exceptional Results* 

---

## Technical Approach

<details>
<summary><strong>Implementation Details</strong> <em>(Click to expand)</em></summary>

<br>

| **Area** | **Techniques Applied** |
|:----------------------:|:-----------------------|
| **Pipeline Arch.** | `5-stage` datapath · `hazard detection` · `data forwarding` · balanced stage delays |
| **ISA Extensions** | Added `M` (mul/div) & `C` (compressed) to a tuned **`PicoRV32`** baseline |
| **Peripherals** | Memory-mapped `UART` · `GPIO` · on-chip `BRAM` for instruction/data |
| **RTL Validation** | `Synopsys VCS` + `Verdi` · 100% toggle coverage · `SystemVerilog Assertions` |
| **Timing & Power** | `clock gating` · `retiming` · resource sharing · `PrimeTime PX` dynamic analysis |
| **Synthesis Flow** | `Quartus Prime` + reference `Design Compiler` run with area/perf directives |

</details>

---

## Key Performance Metrics <sub>(DE1-SoC • Cyclone V)</sub>

<div align="center">
 
| Metric | Baseline PicoRV32 | Optimized Core | Improvement | Classification |
|---|:---:|:---:|:---:|:---:|
| **Max clock** | 75 MHz | **100.15 MHz** | **+34%** | Frequency |
| **Critical-path delay** | 13.3 ns | **9.1 ns** | **-32%** | Timing |
| **Logic elements** | 9,870 | **7,760** | **-21%** | Area |
| **Typical CPI** | 1.85 | **1.21** | **-35%** | Performance |
| **Power @ 100 MHz** | 162 mW | **137 mW** | **-15%** | Power |

</div>

<br>

> **Measured with:**  
> ![Quartus](https://img.shields.io/badge/Quartus-24.1-0071C5?logo=intel&logoColor=white) ![VCS](https://img.shields.io/badge/VCS-2024.03-FFD700?logoColor=black) ![Verdi](https://img.shields.io/badge/Verdi-2024.03-8A2BE2?logoColor=white) ![Icarus](https://img.shields.io/badge/Icarus%20Verilog-11.0-B30000?logoColor=white) ![GTKWave](https://img.shields.io/badge/GTKWave-3.3.115-39FF14?logoColor=black)

---

## Validation & Research Status

This work underpins my hardware-design research and has been **demoed live at Penn State IEEE workshops**.  
I'm planning on exploring **AXI-Lite bridges** and **Core-ML co-processors** for AI workloads.

**Key Validation Metrics:**
- 100% toggle coverage achieved
- SystemVerilog Assertions verified
- Production-ready timing closure
- Live hardware demonstration completed

---

## Quick Start

```bash
# 1. Clone
git clone https://github.com/jeremiah781/Pipelined-RV32IMC-Processor.git
cd Pipelined-RV32IMC-Processor

# 2. Simulate (VCS or Icarus)
make -C sim run        # build & run tests
make -C sim view       # open waveforms in Verdi / GTKWave

# 3. Synthesize & program (Quartus)
quartus_sh --flow compile fpga/rv32imc_top.qpf
quartus_pgm -m jtag -o "p;output_files/rv32imc_top.sof"
```

---

<div align="center">

### **Key Achievements**

**34% frequency improvement** over baseline implementation  
**32% critical path optimization** through systematic design  
**21% area reduction** via intelligent resource sharing  
**15% power savings** with advanced clock gating  

---

<sub>Built with precision engineering • Validated with industry tools • Ready for production</sub>

</div>
