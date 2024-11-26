# Dragon Ball Z: Budokai Tenkaichi 3 Rollback Netcode Implementation

## Overview
This repository works in tandem with a [modded Dolphin emulator repo](https://github.com/dolphin-emu/dolphin) to implement rollback netcode for Dragon Ball Z: Budokai Tenkaichi 3 (BT3) through reverse engineering. 

This repository focuses on reverse engineering Dragon Ball Z: Budokai Tenkaichi 3 and implementing necessary code modifications for rollback netcode support.

The goal is to implement a split-screen battle interface with game state saving, game logic, rendering and sound call separation hooks to allow for rollback implementation while the modded dolphin handles input and networking.

## Open Knowledge, No Gatekeeping

**Important**: This project explicitly rejects gatekeeping and "insider knowledge" culture that has historically hindered BT3's modding scene. If you're someone who hoards knowledge or refuses to share information to maintain some perceived advantage or status - this project is NOT for you. 

What we stand for:
- Open collaboration and knowledge sharing
- Documentation of ALL findings and techniques
- Helping newcomers learn and contribute
- Building a sustainable, growing modding community

What we don't tolerate:
- Gatekeeping information
- Refusing to explain techniques or discoveries
- Creating artificial barriers for new contributors
- "I know something you don't know" attitudes

This project aims to revitalize BT3's modding scene through open collaboration. If you're not on board with this philosophy, please find another project. We're here to build something for everyone, not to stroke egos.

### What This Means in Practice
- Share and document your discoveries
- Make a good faith effort to comment and explain your code
- Share techniques when you understand them
- Welcome questions and help others learn
- Value all contributions, regardless of experience level
- Encourage and support new contributors
- If you're not great at documentation/commenting, that's okay - just try your best and others can help

The goal is to learn and grow together. Not everyone starts as an expert documenter or explainer, but we can all work towards building a more open and helpful community.

## Prerequisites
- [DBZ BT3 Widescreen Tournament ISO 2.1 (Wii)](https://docs.google.com/document/d/1v6EnaYr624Dz-MyNXEdFoJ5FKPLhvAWD08rmHATL3uc/edit?tab=t.0#heading=h.uicrin9d2ldj) - European Version (20% faster)
- Dolphin Emulator 5.0 or later (for reference/forking/debugging)
- [Dolphin Memory Engine](https://github.com/aldelaro5/dolphin-memory-engine) 1.2.4 (for referebce/debugging)
- [Ghidra](https://ghidra-sre.org) 11.2.1

## Technical Architecture

### Game Modifications
- Utilizing unused "Dragon Net Battle" section as entry point for code injection
- Implementing custom interface for netplay battle
- Separating core components:
  - Game logic
  - Rendering pipeline
  - Audio callback system
- Creating hooks for Dolphin emulator interaction

### Dolphin Implementation*

*On the other repo**

Based on Slippi architecture:
- Virtual input device system for netplay opponent
- Input buffer management
- State preservation system
- Rollback implementation:
  - Input difference detection
  - Game state rollback mechanism
  - Logic recalculation
  - Render update system

## Project Roadmap

[Get Started here](Docs/reverse-engineering-guide.md)

### Phase 1: Reverse Engineering
- [ ] Game Logic Analysis
  - [ ] Identify core game mechanics and systems
  - [ ] Map data structures and memory layouts
  - [ ] Document game state management
- [ ] Code Injection Research
  - [ ] Analyze "Dragon Net Battle" section
  - [ ] Identify safe injection points
  - [ ] Document memory constraints
- [ ] Component Separation (if they're already separated we can skip this)
  - [ ] Isolate game logic
  - [ ] Separate rendering pipeline
  - [ ] Extract audio callback system
- [ ] Non-Deterministic Elements Resolution
  - [ ] Handle random elements (ki blasts, scatter shots)
  - [ ] Address character-specific RNG (Mr. Satan's Blast 2)
  - [ ] Document and mitigate seed-dependent behaviors

### Phase 2: Game Modification
- [ ] Code Injection Implementation
  - [ ] Create custom interface in "Dragon Net Battle" section
  - [ ] Implement hook system for Dolphin interaction
  - [ ] Develop state management interface
- [ ] Component Restructuring
  - [ ] Implement separated game logic calls
  - [ ] Create rendering pipeline hooks
  - [ ] Develop audio callback management
- [ ] Interface Development
  - [ ] Create network battle UI
  - [ ] Implement state synchronization hooks
  - [ ] Develop debug interface

### Phase 3: Dolphin Integration
- [ ] Verify rollback game logic stability
  - [ ] RNG based moves calculated correctly when re-simulated
  - [ ] Sound call gets called consistently

### Phase 4: Polish & Testing
- [ ] Alpha Testing
  - Conduct extensive edge-case testing
  - Gather player feedback
  - Document and address stability issues
- [ ] Performance Optimization
  - [ ] Optimize state saving
  - [ ] Improve rollback performance
  - [ ] Minimize network overhead

## Technical Considerations

### Code Injection
- Memory constraints in "Dragon Net Battle" section
- Safe hook points identification
- State preservation requirements
- Interface communication protocol

### Rollback Implementation
The rollback system will:
1. Save and restore game states efficiently
2. Handle input prediction and correction
3. Manage network synchronization
4. Deal with visual and audio discontinuities
5. Recalculate game logic on input mismatch
6. Update renders after state rollback


## Current Status
- Reverse engineering: In Progress
- Code injection research: Not Started
- Dolphin modification: Planning Phase
- Netplay implementation: Not Started

## Contributing
Contributions are welcome! Please feel free to submit pull requests or open issues for discussion.
