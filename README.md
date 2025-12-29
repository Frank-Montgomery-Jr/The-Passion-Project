# Ceiling Fan Troubleshooting Game

## Project Overview

I'm planning to build an interactive educational game where players act as electricians troubleshooting a broken ceiling fan. Instead of a typical multiple-choice quiz, I want to create a real troubleshooting experience where problems are hidden and players have to figure out what's wrong by inspecting different electrical components.

## What I'm Building

The game will feature:

- A ceiling fan that's not working (the main problem)
- Four electrical components that players can inspect
- Hidden problems - players won't know which component is broken
- Interactive repairs where you actually fix things (flip switches, reset breakers, reconnect wires)
- Different difficulty levels with multiple problems to solve

## Why This Project?

I chose this project because:

1. I want to learn JavaScript game development
2. It combines programming with real-world electrical concepts
3. It's more challenging than a basic quiz app
4. I can practice state management and interactive UI design

## Planned Features

### Core Gameplay
- **Difficulty Levels:** Easy (1 problem), Medium (2 problems), Hard (3 problems)
- **Lives System:** Players get 2 lives per problem - if they pick the wrong component, they lose a life
- **Real Troubleshooting:** The problems will be randomized so players have to actually think

### Components to Inspect
1. **Wall Switch** - Check if it's turned on
2. **Circuit Breaker** - See if the breaker has tripped
3. **Junction Box** - Look for loose wire connections
4. **Ceiling Fan** - Check the pull chain position

### Interactive Elements
- Click switches to flip them
- Click breakers to reset them
- Click individual wires to reconnect them (with visual gaps showing which ones are broken)
- Click the pull chain to turn the fan on

### Educational Content
Each component will have information explaining:
- How it works
- What it does in the electrical system
- Safety considerations
- Common problems

## Technical Plan

### Technologies
- **HTML5** for structure
- **CSS3** for styling and animations
- **JavaScript** for game logic (no frameworks - keeping it simple)
- **Web Audio API** for sound effects

### Key Challenges I Expect

1. **State Management:** Keeping track of which problems are active, which are fixed, how many lives remain
2. **Randomization:** Making sure different problems appear each game
3. **Visual Feedback:** Creating good animations for sparks, component repairs, etc.
4. **Wire System:** Making the junction box show visual gaps in broken wires

## Development Phases

### Phase 1: Planning & Design ✓
- [x] Write project requirements
- [x] Create data model
- [x] Design UI mockups
- [x] Plan game flow with UML diagrams

### Phase 2: Basic Structure
- [ ] Set up HTML structure
- [ ] Create component cards layout
- [ ] Build difficulty selection screen
- [ ] Set up CSS grid for components

### Phase 3: Core Game Logic
- [ ] Implement game state management
- [ ] Create difficulty settings (1, 2, or 3 problems)
- [ ] Build random problem selection system
- [ ] Add lives tracking system

### Phase 4: Component Interactions
- [ ] Build inspection modal system
- [ ] Add educational content for each component
- [ ] Create interactive repair interfaces for each component type

### Phase 5: Interactive Repairs
- [ ] Wall switch: clickable toggle animation
- [ ] Circuit breaker: clickable reset with color change
- [ ] Junction box: wire gap system with individual wire clicking
- [ ] Ceiling fan: pull chain with spinning animation

### Phase 6: Feedback Systems
- [ ] Add spark animation for wrong attempts
- [ ] Implement sound effects (electric zap)
- [ ] Create success/error messages
- [ ] Add win/lose screens

### Phase 7: Polish & Testing
- [ ] Refine animations and transitions
- [ ] Test all three difficulty levels
- [ ] Make sure random wire selection works correctly
- [ ] Mobile responsiveness
- [ ] Browser compatibility testing

## Data Structure Plan

The game will track:

```javascript
gameState = {
  difficulty: "easy" | "medium" | "hard",
  currentLives: 2,
  problemsToFix: 1-3,
  problemsFixed: 0,
  activeProblems: ["switch-off", "loose-wires"],
  components: {
    "wall-switch": { hasProblem: true, isFixed: false },
    "circuit-breaker": { hasProblem: false, isFixed: false },
    // etc...
  }
}
```

For the junction box, I'll need special tracking:
- Which wires are broken (red, black, and/or white)
- How many wires have been fixed
- Visual state of each wire (intact, broken, or connected)

## Design Decisions

### Visual Style
I'm going for a retro-industrial look with:
- Dark backgrounds (like electrical panels)
- Orange/gold accent colors (warning colors)
- Clean, technical fonts
- Grid-based layout

### User Experience
- Click to inspect (not hover) - clearer interaction
- Education before action - show info before letting them try to fix
- Visual problems - players should be able to SEE the issues (gaps in wires, red breakers)
- Clear feedback - sparks and sound when wrong, success message when right

### Safety Theme
I want to emphasize electrical safety throughout:
- "Always turn off power" warnings
- Sparks represent the danger of working on live circuits
- Professional electrician mottos displayed
- Safety information in each component's description

## Success Criteria

I'll know the project is successful when:

1. All three difficulty levels work correctly
2. Problems are truly hidden and require troubleshooting
3. The interactive repairs feel satisfying to use
4. Players learn something about electrical systems
5. The wire gap system clearly shows which wires need fixing
6. The game is playable without instructions

## Timeline

- **Week 1:** Complete planning documents (requirements, data model, UI design, UML)
- **Week 2:** Build basic structure and game logic
- **Week 3:** Implement interactive components and animations
- **Week 4:** Polish, test, and finalize

## Resources & References

- Electrical safety guidelines
- JavaScript game development tutorials
- CSS animation references
- Web Audio API documentation

## Project Structure

This repository will be organized as follows:

```
ceiling-fan-game/
│
├── index.html                      # Main game file
│
├── README.md                       # This file - project blueprint
│
├── docs/                          # Documentation folder
│   ├── REQUIREMENTS-UPDATED.md    # Project requirements
│   ├── DATA-MODEL.md              # Data structures and relationships
│   ├── UI-DESIGN-DOCUMENT.md      # User interface specifications
│   ├── UML-DIAGRAMS.md            # UML diagrams (text format)
│   ├── class-diagram.png          # UML Class Diagram
│   ├── state-diagram.png          # UML State Diagram
│   └── sequence-diagram.png       # UML Sequence Diagram
│
└── (Additional files will be added during development)
```

### File Descriptions

- **index.html** - The main game application (all HTML/CSS/JS in one file)
- **README.md** - Project overview, plan, and development roadmap
- **docs/** - All planning and design documentation
  - Requirements document defines what the game should do
  - Data model shows how information is structured
  - UI design document details the visual interface
  - UML diagrams illustrate the technical architecture

## Notes to Self

Things I need to remember:
- Keep the code clean and commented
- Test each difficulty level thoroughly
- Make sure the lives reset after each successful fix
- The junction box randomization needs to pick 1-2 wires (not all 3)
- Don't forget the win animation (fan spinning)

## Questions to Resolve

- Should lives reset after each problem or carry over? **Decision: Reset per problem**
- How many wires should be broken in junction box? **Decision: Random 1-2 wires**
- What happens if player runs out of lives? **Decision: Game over screen, try again**

---

**Status:** Currently in planning phase  
**Next Step:** Begin Phase 2 - Basic Structure  
**Expected Completion:** 4 weeks from start
