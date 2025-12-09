---
title: Physical Layer
module_number: 2
description: Physical transmission media, encoding techniques, and physical layer devices
---

## Overview

The physical layer is the first layer of the OSI model, responsible for the physical transmission of raw bits over a communication channel.

## Learning Objectives

After completing this module, you should be able to:

- Understand different types of transmission media
- Explain signal encoding and modulation techniques
- Describe physical layer devices and their functions
- Analyze bandwidth and data rate calculations

## Transmission Media

### Guided Media (Wired)

**1. Twisted Pair Cable**
- Two insulated copper wires twisted together
- Types:
  - **Unshielded Twisted Pair (UTP)**: Most common, used in Ethernet
  - **Shielded Twisted Pair (STP)**: Better noise immunity
- Categories: Cat5, Cat5e, Cat6, Cat6a, Cat7
- Maximum distance: ~100 meters

**2. Coaxial Cable**
- Central conductor surrounded by insulation and shield
- Better shielding than twisted pair
- Used in cable TV and older Ethernet networks
- Higher bandwidth than twisted pair

**3. Fiber Optic Cable**
- Transmits data as light pulses
- Types:
  - **Single-mode**: Long distances, laser light source
  - **Multi-mode**: Short distances, LED light source
- Advantages:
  - Very high bandwidth
  - Immune to electromagnetic interference
  - Long distance transmission
  - Secure (difficult to tap)
- Disadvantages:
  - More expensive
  - Requires specialized equipment

### Unguided Media (Wireless)

**1. Radio Waves**
- Omnidirectional propagation
- Can penetrate walls
- Used in: Wi-Fi, Bluetooth, cellular networks
- Frequency ranges: 3 kHz to 1 GHz

**2. Microwaves**
- Directional transmission
- Requires line of sight
- Used in: Satellite communication, point-to-point links
- Frequency ranges: 1 GHz to 300 GHz

**3. Infrared**
- Short-range communication
- Cannot penetrate walls
- Used in: Remote controls, IrDA
- Frequency ranges: 300 GHz to 400 THz

## Signal Encoding

Encoding is the process of converting data into signals for transmission.

### Digital Encoding Schemes

**1. Non-Return to Zero (NRZ)**
- High voltage = 1, Low voltage = 0
- Simple but synchronization issues

**2. Manchester Encoding**
- Used in Ethernet (10 Mbps)
- Transition in middle of each bit period
- 0 = high-to-low transition
- 1 = low-to-high transition

**3. Differential Manchester**
- Transition at start of bit = 0
- No transition at start = 1
- Better noise immunity

## Bandwidth and Data Rate

### Key Concepts

- **Bandwidth**: Range of frequencies a channel can carry (measured in Hz)
- **Data Rate**: Number of bits transmitted per second (measured in bps)
- **Baud Rate**: Number of signal changes per second

### Nyquist Theorem

For noiseless channel:
```
Maximum Data Rate = 2 × Bandwidth × log₂(L)
```
Where L = number of signal levels

### Shannon Capacity

For noisy channel:
```
Channel Capacity = Bandwidth × log₂(1 + SNR)
```
Where SNR = Signal-to-Noise Ratio

## Physical Layer Devices

### Hub
- Layer 1 device
- Broadcasts data to all connected devices
- No intelligence or filtering
- Creates single collision domain

### Repeater
- Regenerates and amplifies signals
- Extends network distance
- No data interpretation

### Network Interface Card (NIC)
- Connects computer to network
- Has unique MAC address
- Converts parallel data to serial

## Multiplexing

Multiplexing allows multiple signals to share a single transmission medium.

### Types of Multiplexing

**1. Frequency Division Multiplexing (FDM)**
- Different signals use different frequencies
- Used in: Radio, TV broadcasting

**2. Time Division Multiplexing (TDM)**
- Different signals use different time slots
- Used in: Digital telephony

**3. Wavelength Division Multiplexing (WDM)**
- Used in fiber optic networks
- Multiple wavelengths of light

**4. Code Division Multiplexing (CDM)**
- Used in cellular networks (CDMA)
- Unique codes for each signal

## Summary

The physical layer provides the foundation for all network communication. Understanding transmission media, encoding techniques, and physical layer concepts is essential for network design and troubleshooting.

## Key Terms

- **Attenuation**: Signal strength loss over distance
- **Interference**: Unwanted signals affecting transmission
- **Throughput**: Actual data rate achieved
- **Propagation Delay**: Time for signal to travel from source to destination

## Exercises

1. Calculate the maximum data rate for a channel with 4 signal levels and 3000 Hz bandwidth
2. Compare the advantages and disadvantages of fiber optic vs. twisted pair cable
3. Explain why Manchester encoding is better than NRZ for synchronization
4. Research current fiber optic technology speeds and distances
