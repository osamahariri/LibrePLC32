<p align="center">
  <img src="img/logo.png" alt="LibrePLC32 logo" width="360">
</p>

# LibrePLC32

**LibrePLC32** is an open-source, KiCad-based Programmable Logic Controller (PLC) hardware project.

The goal of the project is to create a compact, hackable, and well-documented PLC platform for industrial automation experiments, prototyping, education, and open hardware development.

> ⚠️ **Work in progress:** LibrePLC32 is currently under development.

## Project goals

LibrePLC32 aims to provide:

- An open hardware PLC design
- KiCad source files for schematic and PCB development
- Field-oriented interfaces such as digital I/O, CAN, RS-485, and Ethernet
- A design that can be studied, modified, repaired, and improved by the community
- Documentation for design decisions and component calculations

## Repository structure

```text
.
├── img/              # Project logo and graphics
├── plc/
│   ├── docs/         # Design notes and calculations
│   └── kicad/        # KiCad project, schematics, PCB, and libraries
├── LICENSE
└── README.md