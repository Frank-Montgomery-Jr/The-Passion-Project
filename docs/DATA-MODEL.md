# Ceiling Fan Troubleshooting Game
## Data Model Documentation

---

## Overview

This document defines all data structures, objects, and state management for the Ceiling Fan Troubleshooting Game. The data model represents the information the game needs to track and how it's organized.

---

## Core Data Structures

### 1. Game State Object

The central object that tracks the current state of the game.

```javascript
const gameState = {
  // Game Settings
  difficulty: "easy",              // Type: String ("easy", "medium", "hard")
  problemsToFix: 1,                // Type: Number (1, 2, or 3)
  
  // Player Progress
  lives: 2,                        // Type: Number (0-2)
  problemsFixed: 0,                // Type: Number (0 to problemsToFix)
  
  // Game Status
  isGameStarted: false,            // Type: Boolean
  isGameOver: false,               // Type: Boolean
  hasWon: false,                   // Type: Boolean
  
  // Current Problems
  activeProblems: [],              // Type: Array of problem IDs
                                   // Example: ["switch-off", "breaker-tripped"]
  
  // UI State
  currentInspection: null,         // Type: String (component ID) or null
  showModal: false,                // Type: Boolean
  statusMessage: ""                // Type: String
};
```

**Properties Explained:**

| Property | Type | Purpose | Possible Values |
|----------|------|---------|-----------------|
| `difficulty` | String | Selected game difficulty | "easy", "medium", "hard" |
| `problemsToFix` | Number | Total problems to solve | 1 (easy), 2 (medium), 3 (hard) |
| `lives` | Number | Remaining attempts | 0, 1, 2 |
| `problemsFixed` | Number | Problems successfully fixed | 0 to problemsToFix |
| `isGameStarted` | Boolean | Has game begun? | true, false |
| `isGameOver` | Boolean | Game ended? | true, false |
| `hasWon` | Boolean | Player won? | true, false |
| `activeProblems` | Array | Current problems in game | Array of problem IDs |
| `currentInspection` | String/null | Component being inspected | component ID or null |
| `showModal` | Boolean | Display inspection popup? | true, false |
| `statusMessage` | String | Feedback message to player | Any text |

---

### 2. Component Object

Represents each electrical component in the game.

```javascript
const component = {
  // Identity
  id: "wall-switch",               // Type: String (unique identifier)
  name: "Wall Switch",             // Type: String (display name)
  icon: "💡",                      // Type: String (emoji or image path)
  
  // Status
  hasProblem: false,               // Type: Boolean
  isFixed: false,                  // Type: Boolean
  isInspected: false,              // Type: Boolean
  
  // Problem Details
  problemType: null,               // Type: String or null (problem ID)
  
  // Educational Content
  educationalText: "⚠️ Safety First: Always check the wall switch first! The wall switch controls power flow to the ceiling fan. If it's in the OFF position, no electricity reaches the fan.",
  
  // Position (for UI layout)
  position: {
    gridArea: "top-left"           // Type: String (CSS grid area)
  }
};
```

**Component Properties:**

| Property | Type | Purpose | Example Value |
|----------|------|---------|---------------|
| `id` | String | Unique identifier | "wall-switch" |
| `name` | String | Display name | "Wall Switch" |
| `icon` | String | Visual representation | "💡" or "assets/switch.png" |
| `hasProblem` | Boolean | Has active problem? | true, false |
| `isFixed` | Boolean | Problem been fixed? | true, false |
| `isInspected` | Boolean | Player clicked it? | true, false |
| `problemType` | String/null | Which problem it has | "switch-off" or null |
| `educationalText` | String | Teaching content | Safety information |
| `position` | Object | UI placement | Grid coordinates |

---

### 3. Components Collection

Array of all four game components.

```javascript
const components = [
  {
    id: "ceiling-fan",
    name: "Ceiling Fan",
    icon: "🌀",
    hasProblem: false,
    isFixed: false,
    isInspected: false,
    problemType: null,
    educationalText: "🌀 Most ceiling fans have a pull chain that acts as an on/off switch. Even if power is flowing to the fan, if the chain is in the OFF position, the fan won't spin.",
    position: { gridArea: "top-center" }
  },
  {
    id: "wall-switch",
    name: "Wall Switch",
    icon: "💡",
    hasProblem: false,
    isFixed: false,
    isInspected: false,
    problemType: null,
    educationalText: "⚠️ Safety First: Always check the wall switch first! The wall switch controls power flow to the ceiling fan. If it's in the OFF position, no electricity reaches the fan.",
    position: { gridArea: "bottom-left" }
  },
  {
    id: "circuit-breaker",
    name: "Circuit Breaker Panel",
    icon: "⚡",
    hasProblem: false,
    isFixed: false,
    isInspected: false,
    problemType: null,
    educationalText: "⚡ Circuit breakers protect your home from electrical overload. When too much current flows through a circuit, the breaker 'trips' (turns off) to prevent fires and damage.",
    position: { gridArea: "bottom-right" }
  },
  {
    id: "junction-box",
    name: "Junction Box",
    icon: "🔌",
    hasProblem: false,
    isFixed: false,
    isInspected: false,
    problemType: null,
    educationalText: "🔌 The junction box is where electrical connections are made. Loose wire connections can cause intermittent power issues or complete failure. Always ensure connections are tight!",
    position: { gridArea: "top-right" }
  }
];
```

---

### 4. Problem Definition Object

Defines each possible problem and its solutions.

```javascript
const problemDefinition = {
  // Identity
  id: "switch-off",                // Type: String (unique identifier)
  componentId: "wall-switch",      // Type: String (which component has this problem)
  
  // Description
  name: "Wall Switch is OFF",      // Type: String (problem name)
  description: "The wall switch is in the OFF position, preventing power from reaching the ceiling fan.",
  
  // Solutions
  correctFix: {
    text: "Flip the switch to ON position",
    explanation: "Turning the switch ON allows electricity to flow to the ceiling fan."
  },
  
  wrongFixes: [
    {
      text: "Replace the wall switch",
      explanation: "The switch isn't broken - it just needs to be turned ON!"
    },
    {
      text: "Check the switch wiring",
      explanation: "The wiring is fine - the switch is simply in the OFF position."
    }
  ]
};
```

**Problem Properties:**

| Property | Type | Purpose | Example |
|----------|------|---------|---------|
| `id` | String | Unique problem identifier | "switch-off" |
| `componentId` | String | Which component has problem | "wall-switch" |
| `name` | String | Problem display name | "Wall Switch is OFF" |
| `description` | String | What's wrong | Explanation text |
| `correctFix` | Object | Right solution | {text, explanation} |
| `wrongFixes` | Array | Wrong solutions | Array of {text, explanation} |

---

### 5. Problems Collection

Array of all four possible problems in the game.

```javascript
const problems = [
  {
    id: "switch-off",
    componentId: "wall-switch",
    name: "Wall Switch is OFF",
    description: "The wall switch is in the OFF position, preventing power from reaching the ceiling fan.",
    correctFix: {
      text: "Flip the switch to ON position",
      explanation: "Turning the switch ON allows electricity to flow to the ceiling fan."
    },
    wrongFixes: [
      {
        text: "Replace the wall switch",
        explanation: "The switch isn't broken - it just needs to be turned ON!"
      },
      {
        text: "Check the switch wiring",
        explanation: "The wiring is fine - the switch is simply in the OFF position."
      }
    ]
  },
  {
    id: "breaker-tripped",
    componentId: "circuit-breaker",
    name: "Circuit Breaker Tripped",
    description: "The bedroom circuit breaker has tripped (turned OFF), cutting power to the fan circuit.",
    correctFix: {
      text: "Reset the bedroom circuit breaker",
      explanation: "Resetting the breaker restores power to the bedroom circuit, including the ceiling fan."
    },
    wrongFixes: [
      {
        text: "Replace the circuit breaker",
        explanation: "The breaker is working correctly - it just needs to be reset!"
      },
      {
        text: "Increase the breaker amperage",
        explanation: "Increasing amperage is dangerous! The breaker just needs to be reset."
      }
    ]
  },
  {
    id: "loose-wires",
    componentId: "junction-box",
    name: "Loose Wire Connections",
    description: "Wire connections inside the junction box have become loose, interrupting the electrical circuit.",
    correctFix: {
      text: "Tighten all wire connections",
      explanation: "Securing loose connections restores proper electrical flow to the ceiling fan."
    },
    wrongFixes: [
      {
        text: "Replace all the wiring",
        explanation: "The wires themselves are fine - they just need to be tightened!"
      },
      {
        text: "Add more wire nuts",
        explanation: "Adding more wire nuts won't help - the existing connections just need tightening."
      }
    ]
  },
  {
    id: "chain-off",
    componentId: "ceiling-fan",
    name: "Pull Chain is OFF",
    description: "The ceiling fan's pull chain is in the OFF position, preventing the fan from operating.",
    correctFix: {
      text: "Pull the chain to turn ON the fan",
      explanation: "Pulling the chain engages the fan's internal switch, allowing it to run."
    },
    wrongFixes: [
      {
        text: "Replace the fan motor",
        explanation: "The motor is fine - the pull chain just needs to be pulled!"
      },
      {
        text: "Check the fan capacitor",
        explanation: "The capacitor is working - you just need to turn the fan ON with the pull chain."
      }
    ]
  }
];
```

---

### 6. Difficulty Configuration Object

Defines settings for each difficulty level.

```javascript
const difficultyConfig = {
  easy: {
    level: "easy",
    displayName: "🟢 Easy",
    problemCount: 1,
    lives: 2,
    description: "One problem to find and fix"
  },
  medium: {
    level: "medium",
    displayName: "🟠 Medium",
    problemCount: 2,
    lives: 2,
    description: "Two problems to find and fix"
  },
  hard: {
    level: "hard",
    displayName: "🔴 Hard",
    problemCount: 3,
    lives: 2,
    description: "Three problems to find and fix"
  }
};
```

---

## Data Relationships

### Entity Relationship Diagram

```
┌─────────────────┐
│   Game State    │
│                 │
│ - difficulty    │────┐
│ - lives         │    │
│ - problemsFixed │    │
│ - activeProblems│────┼────────────┐
└─────────────────┘    │            │
                       │            │
                       ▼            ▼
              ┌─────────────┐  ┌──────────────┐
              │ Difficulty  │  │   Problems   │
              │   Config    │  │  Collection  │
              └─────────────┘  └──────┬───────┘
                                      │
                                      │ problemType
                                      │
                                      ▼
                              ┌───────────────┐
                              │  Components   │
                              │  Collection   │
                              │               │
                              │ - ceiling-fan │
                              │ - wall-switch │
                              │ - breaker     │
                              │ - junction-box│
                              └───────────────┘
```

**Relationships:**
- `gameState.difficulty` → references `difficultyConfig`
- `gameState.activeProblems` → array of problem IDs from `problems`
- `component.problemType` → references a problem from `problems`
- Each `problem.componentId` → references a component from `components`

---

## Data Flow Examples

### Example 1: Starting a New Game (Easy Mode)

```javascript
// Initial State
gameState = {
  difficulty: null,
  lives: 2,
  problemsToFix: 0,
  problemsFixed: 0,
  isGameStarted: false,
  activeProblems: [],
  // ...
};

// After clicking "Easy" difficulty
gameState = {
  difficulty: "easy",
  lives: 2,
  problemsToFix: 1,
  problemsFixed: 0,
  isGameStarted: true,
  activeProblems: ["switch-off"],  // Randomly selected
  // ...
};

// Component updated
components[1] = {
  id: "wall-switch",
  hasProblem: true,
  problemType: "switch-off",
  // ...
};
```

### Example 2: Player Inspects Component

```javascript
// Player clicks "Wall Switch"
gameState.currentInspection = "wall-switch";
gameState.showModal = true;

components[1].isInspected = true;

// Modal displays:
// - educationalText from component
// - correctFix and wrongFixes from problem
```

### Example 3: Player Chooses Correct Fix

```javascript
// Before fix
gameState = {
  lives: 2,
  problemsFixed: 0,
  problemsToFix: 1,
  // ...
};

components[1] = {
  id: "wall-switch",
  hasProblem: true,
  isFixed: false,
  // ...
};

// After correct fix
gameState = {
  lives: 2,              // No change
  problemsFixed: 1,      // Incremented
  problemsToFix: 1,
  hasWon: true,          // All problems fixed!
  statusMessage: "Great job! Wall Switch fixed!"
};

components[1] = {
  id: "wall-switch",
  hasProblem: true,
  isFixed: true,         // Now fixed
  // ...
};
```

### Example 4: Player Chooses Wrong Fix

```javascript
// Before wrong answer
gameState.lives = 2;

// After wrong answer
gameState.lives = 1;              // Decremented
gameState.statusMessage = "That wasn't the right fix! Try inspecting another component.";

// Component remains unfixed
components[1].isFixed = false;
```

---

## State Management Functions

### Core Functions That Modify Data

```javascript
// Initialize new game
function initializeGame(difficulty) {
  // Sets gameState.difficulty
  // Sets gameState.problemsToFix based on difficulty
  // Randomly selects problems for gameState.activeProblems
  // Updates components with hasProblem and problemType
}

// Handle component inspection
function inspectComponent(componentId) {
  // Sets gameState.currentInspection
  // Sets gameState.showModal = true
  // Marks component.isInspected = true
}

// Process fix attempt
function attemptFix(componentId, selectedFix) {
  // Checks if selectedFix is correct
  // If correct:
  //   - Sets component.isFixed = true
  //   - Increments gameState.problemsFixed
  //   - Checks for win condition
  // If wrong:
  //   - Decrements gameState.lives
  //   - Checks for game over condition
}

// Check win condition
function checkWinCondition() {
  // Returns true if gameState.problemsFixed === gameState.problemsToFix
}

// Check game over condition
function checkGameOverCondition() {
  // Returns true if gameState.lives === 0
}

// Reset game
function resetGame() {
  // Resets all gameState properties to initial values
  // Resets all component properties
}
```

---

## Data Validation Rules

### Game State Rules
- `lives`: Must be between 0 and 2
- `problemsFixed`: Cannot exceed `problemsToFix`
- `problemsToFix`: Must be 1, 2, or 3
- `difficulty`: Must be "easy", "medium", or "hard"
- `activeProblems`: Length must equal `problemsToFix`

### Component Rules
- Each component can have only one problem at a time
- `isFixed` can only be true if `hasProblem` is true
- `problemType` must match a valid problem ID or be null

### Problem Rules
- Each `problemDefinition.componentId` must match an existing component
- `wrongFixes` array must contain exactly 2 items
- All problem IDs must be unique

---

## Data Persistence

**Current Implementation:**
- Data is **NOT persisted** (resets on page refresh)
- All data lives in memory during game session

**Future Enhancement:**
```javascript
// Save game state to localStorage
function saveGameState() {
  localStorage.setItem('ceilingFanGame', JSON.stringify(gameState));
}

// Load game state from localStorage
function loadGameState() {
  const saved = localStorage.getItem('ceilingFanGame');
  return saved ? JSON.parse(saved) : null;
}
```

---

## Summary

### Total Data Objects:
1. **Game State** (1 object) - Tracks current game progress
2. **Components** (4 objects) - Electrical components to inspect
3. **Problems** (4 objects) - Possible issues to fix
4. **Difficulty Config** (3 objects) - Settings for each level

### Key Data Operations:
- **Initialize Game** - Set up difficulty and problems
- **Inspect Component** - View component details
- **Attempt Fix** - Try to solve a problem
- **Update Lives** - Decrement on wrong answer
- **Check Win/Loss** - Determine game outcome
- **Reset Game** - Start over

---

*Data Model Version: 1.0*  
*Last Updated: December 2024*
