# Ceiling Fan Troubleshooting Game
## Educational Interactive Game - Project Requirements

**Project Type:** Web-Based Educational Game  
**Platform:** Browser (HTML/CSS/JavaScript)  
**Target Audience:** Students learning electrical troubleshooting  
**Version:** 2.0 - Interactive Troubleshooting Mode

---

## Assignment Overview

Build an educational web-based game that teaches electrical troubleshooting skills through realistic, hands-on interactive gameplay. Players take on the role of an electrician tasked with diagnosing and fixing a malfunctioning ceiling fan. Unlike traditional multiple-choice quizzes, players must **find hidden problems** through systematic inspection and **physically interact** with components to repair them - mimicking real-world electrical troubleshooting.

---

## Learning Objectives

- **Systematic Troubleshooting**: Learn to methodically inspect components to identify hidden problems
- **Electrical Safety**: Understand the importance of turning off power before repairs
- **Component Knowledge**: Learn about switches, circuit breakers, junction boxes, and fan controls
- **Visual Diagnosis**: Recognize visual indicators of electrical problems (tripped breakers, disconnected wires)
- **Hands-On Skills**: Practice interactive repairs through direct manipulation of components
- **Problem-Solving**: Apply logical reasoning to determine which component has the issue
- **Safety Consequences**: Experience realistic feedback (sparks) for unsafe practices

---

## Project Structure

```
ceiling-fan-game/
├── troubleshooting-game-final.html    - Complete single-file game
├── REQUIREMENTS.md                     - This document
├── DATA-MODEL.md                       - Data structures documentation
├── README.md                           - Setup and play instructions
└── assets/                             - (Optional) External images if needed
```

**Note:** Current implementation uses a single HTML file containing embedded CSS and JavaScript for portability.

---

## Core Game Mechanics

### 1. Difficulty Selection
Players choose from three difficulty levels at the start:

- **🟢 Easy Mode**: 1 hidden problem | 2 Lives
- **🟠 Medium Mode**: 2 hidden problems | 2 Lives Per Problem (4 total)
- **🔴 Hard Mode**: 3 hidden problems | 2 Lives Per Problem (6 total)

### 2. Lives-Per-Problem System
- Each problem gets **2 lives** (2 attempts)
- Wrong component selection costs 1 life
- Lives **RESET to 2** after successfully fixing each problem
- Running out of lives on any problem = Game Over
- Visual display: ❤️❤️ (hearts)

### 3. Problem Categories
The game randomly selects from four possible electrical problems:

1. **Wall Switch OFF** - Switch in DOWN position, blocking power flow
2. **Circuit Breaker Tripped** - Bedroom breaker in RED/OFF position
3. **Loose Wire Connections** - 1-2 wires disconnected with **visible gaps** (randomized)
4. **Pull Chain OFF** - Fan's pull chain not engaged

**Key Feature:** Problems are **HIDDEN** - players cannot tell which component is broken just by looking. They must inspect each one and use troubleshooting logic.

---

## Game Flow

### Phase 1: Welcome Screen
1. Display title with electrician mottos:
   - "Always Carry the Right Tools for the Job"
   - "No Matter The Load, We Do It By Code"
2. Show game scenario and rules
3. **Safety Warning:** "Make sure power is off before attempting to work on problem"
4. Player selects difficulty level (Easy/Medium/Hard)

### Phase 2: Problem Generation
1. System randomly selects problems based on difficulty
2. Problems are assigned to components (hidden from player)
3. For junction box: Randomly determines 1-2 broken wires
4. Main game screen loads with all 4 components visible

### Phase 3: Real Troubleshooting
**The player DOES NOT KNOW which component has the problem!**

1. **Inspect Components:** Player clicks on components to inspect them
   - Ceiling Fan 🌀
   - Junction Box 🔌
   - Wall Switch 💡
   - Circuit Breaker Panel ⚡

2. **Educational Content:** Modal displays teaching about the component
   - Purpose and function
   - Safety information
   - How it works in the electrical system
   - "Attempt Repair →" button

3. **Interactive Repair:** Player sees the component and attempts to fix it
   - **Switch:** Click toggle to flip from OFF to ON
   - **Breaker:** Click red breaker to reset to green
   - **Junction Box:** Click wires with visible GAPS to reconnect them
   - **Fan:** Click pull chain to turn fan ON

### Phase 4: Resolution

**If CORRECT Component:**
- ✅ Visual repair animation (switch flips, breaker resets, wires connect, fan spins)
- Success message: "✅ CORRECT! Problem FIXED!"
- Component marked with green border
- Lives RESET to 2 for next problem
- Progress updates: "1 / 2 problems fixed"

**If WRONG Component:**
- ⚡ **SPARK ANIMATION** with electric zap sound effect
- Error message: "⚡ YOU DIDN'T TURN OFF THE POWER! Wrong component! Lives: 1"
- Lose 1 life
- Must try another component

**If Out of Lives:**
- Game Over screen
- "💥 GAME OVER! You ran out of lives!"
- Option to restart

**If All Problems Fixed:**
- Fan spins on main screen
- Win screen displays
- "🎉 SUCCESS! You fixed all the problems!"
- Option to play again

---

## Technical Requirements

### 1. Core Technologies
- **HTML5**: Semantic structure, modals, grid layout
- **CSS3**: Animations, transitions, responsive design, gradient effects
- **JavaScript ES6+**: Game logic, state management, event handling, Web Audio API

### 2. Key Features Implemented

#### Interactive Components
- **Wall Switch:** Animated toggle (OFF ↔ ON states)
- **Circuit Breaker Panel:** 4 breakers, bedroom breaker can be tripped (red) or on (green)
- **Junction Box:** 3 wires (red, black, white) with visual gap system
  - Broken wires: Two segments separated by visible gap with pulsing indicator
  - Intact wires: Continuous solid line
  - Connected wires: Segments joined with wire nut appearing
- **Ceiling Fan:** Pull chain with spinning blade animation when ON

#### Visual Effects
- Spark animation: 20 golden particles exploding from center
- Wire reconnection: Segments slide together smoothly
- Component state changes: Color transitions, glow effects
- Background: Animated grid pattern
- Modal pop-ups: Slide-up animations

#### Audio Effects
- Electric zap sound (Web Audio API - synthesized)
- Plays on wrong component selection with sparks

#### State Management
- Lives tracking with reset-per-problem system
- Component state (hasProblem, isFixed)
- Wire state tracking (brokenWires array, wiresFixed counter)
- Progress tracking (problemsFixed / problemsToFix)

#### Responsive Design
- Works on desktop and mobile
- Touch-friendly buttons and components
- Adaptive grid layout

### 3. Code Quality
- ✅ Clean, organized single-file structure
- ✅ Commented code explaining key logic
- ✅ Consistent naming conventions (camelCase)
- ✅ Reusable functions
- ✅ Event-driven architecture
- ✅ No console errors

---

## Educational Content

Each component includes safety-first educational text:

### Wall Switch
> "⚠️ Safety First: Always check the wall switch first! The wall switch controls power flow to the ceiling fan. If it's in the OFF position, no electricity reaches the fan. Switches are simple mechanical devices that complete or break the electrical circuit."

### Circuit Breaker Panel
> "⚡ Circuit breakers protect your home from electrical overload. When too much current flows through a circuit, the breaker 'trips' (turns off) to prevent fires and damage. The bedroom breaker controls power to the ceiling fan circuit."

### Junction Box
> "🔌 The junction box is where electrical connections are made. Loose wire connections can cause intermittent power issues or complete failure. All connections must be tight and secure with proper wire nuts. Look carefully - you may see gaps in the wires where they're disconnected!"

### Ceiling Fan
> "🌀 Most ceiling fans have a pull chain that acts as an on/off switch. Even if power is flowing to the fan, if the chain is in the OFF position, the fan won't spin. The pull chain completes the internal circuit that powers the motor."

---

## Wire Randomization System

### Junction Box Behavior
When junction box is the problem:
- **70% Probability:** 1 wire broken
- **30% Probability:** 2 wires broken
- Randomly selected from: red, black, white
- Different combination each game

### Visual Representation
**Broken Wire:**
```
=====  •  =====  ← Gap with pulsing indicator
```

**Intact Wire:**
```
=============     ← Continuous, not clickable
```

**Connected Wire:**
```
======🟠======    ← Wire nut appears, glows
```

---

## Safety Theme Integration

The game emphasizes electrical safety through:

1. **Pre-Game Warning:** "Make sure power is off before attempting to work on problem"
2. **Wrong Attempt Consequences:** Sparks represent touching live circuits
3. **Safety Message:** "YOU DIDN'T TURN OFF THE POWER!" reinforces the danger
4. **Educational Content:** Every component explains safety considerations
5. **Professional Mottos:** Displayed on main screen

---

## Evaluation Criteria

### Functionality (40%)
- ✅ All three difficulty levels work correctly
- ✅ All four problems can be generated and fixed
- ✅ Lives-per-problem system functions properly
- ✅ Wire randomization works (1-2 wires, different each time)
- ✅ Win and lose conditions trigger correctly
- ✅ All components are clickable and interactive
- ✅ Real troubleshooting - player must find hidden problems
- ✅ Interactive repairs work (switches flip, breakers reset, wires connect)
- ✅ Fan spinning animation triggers on win

### Code Quality (25%)
- ✅ Clean, organized code structure
- ✅ Meaningful variable and function names
- ✅ Comments explaining key logic
- ✅ No redundant or dead code
- ✅ Proper use of JavaScript ES6+ features
- ✅ Efficient state management

### User Experience (20%)
- ✅ Intuitive interface - no instructions needed
- ✅ Clear visual feedback (sparks, animations, color changes)
- ✅ Professional retro-industrial design aesthetic
- ✅ Smooth animations and transitions
- ✅ Responsive layout
- ✅ Audio feedback enhances experience

### Educational Value (15%)
- ✅ Accurate electrical safety information
- ✅ Clear safety messaging throughout
- ✅ Engaging troubleshooting methodology
- ✅ Teaches systematic problem-solving
- ✅ Reinforces learning through hands-on interaction
- ✅ Real-world applicability

---

## Unique Features

### What Makes This Game Special:

1. **Real Troubleshooting** - Problems are hidden, not revealed
2. **Interactive Repairs** - Direct manipulation, not multiple choice
3. **Visual Problem Indicators** - See gaps in wires, red breakers, OFF switches
4. **Lives-Per-Problem System** - Get fresh chances for each new problem
5. **Wire Randomization** - Different junction box scenarios each game
6. **Spark Effects** - Realistic consequence for wrong attempts with sound
7. **Professional Theme** - Electrician mottos and safety messaging
8. **Educational First** - Learn before attempting repairs
9. **Progressive Difficulty** - Scales from 1 to 3 problems
10. **Single-File Implementation** - Easy to distribute and grade

---

## Technical Achievements

- **Web Audio API:** Synthesized electric zap sound (no external files)
- **CSS Animations:** 20+ animation effects (sparks, spinning, sliding, glowing)
- **State Management:** Complex game state with lives-per-problem tracking
- **Dynamic UI Generation:** Junction box wires generated programmatically
- **Randomization Engine:** Fair problem selection and wire distribution
- **Modal System:** Multi-step educational and repair workflow
- **Visual Feedback:** Comprehensive player guidance through color and animation

---

## Future Enhancements (Optional)

- 🎵 Additional sound effects (fan spinning, switch clicks, breaker resets)
- ⏱️ Timer mode for speed challenges
- 📊 Score tracking and high scores
- 💾 Progress saving (localStorage)
- 🎯 Achievement system
- 📱 Enhanced mobile optimization
- 🌐 Multiple language support
- 🎨 Alternative visual themes
- 📈 Performance analytics dashboard
- 🔊 Voiceover explanations

---

## Success Metrics

Your game will be considered successful when:
- ✅ Player can complete all three difficulty levels
- ✅ All educational content is accurate and clear
- ✅ Interface is intuitive without written instructions
- ✅ Animations are smooth and professional
- ✅ Code is clean, commented, and well-documented
- ✅ Game teaches real electrical troubleshooting skills
- ✅ Players understand safety principles after playing
- ✅ Different wire configurations appear across multiple plays

---

## Tips for Instructors/Reviewers

**To Test The Game:**
1. Open `troubleshooting-game-final.html` in a modern browser
2. Try all three difficulty levels
3. Intentionally choose wrong components to see spark effects
4. For junction box: Note that wire gaps are visible - this is intentional!
5. Observe that lives reset after fixing each problem
6. Check that different wires are broken across multiple games

**Key Points to Evaluate:**
- Real troubleshooting (problems hidden from player)
- Interactive repairs (not quiz-style multiple choice)
- Visual wire gaps system (junction box shows breaks)
- Lives-per-problem system (resets after each fix)
- Educational content before repairs
- Safety messaging and consequences

---

## Project Philosophy

This game embodies the principle that **learning by doing** is more effective than passive instruction. By requiring players to:
- **Inspect** components systematically
- **Diagnose** problems through observation
- **Repair** issues with direct interaction
- **Experience consequences** of wrong choices

...the game creates a memorable, engaging learning experience that teaches both technical knowledge and safety practices in a way that traditional educational methods cannot match.

---

**Document Version:** 2.0  
**Last Updated:** December 2024  
**Game Status:** Fully Functional & Production Ready  
**File:** troubleshooting-game-final.html

---

*"Always Carry the Right Tools for the Job. No Matter The Load, We Do It By Code."*
