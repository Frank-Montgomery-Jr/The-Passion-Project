# Ceiling Fan Troubleshooting Game
## User Interface Design Document

**Project:** Educational Interactive Troubleshooting Game  
**Version:** 2.0  
**Document Type:** UI/UX Specification  
**Last Updated:** December 2024

---

## Table of Contents

1. [Design Philosophy](#design-philosophy)
2. [Visual Design System](#visual-design-system)
3. [Screen-by-Screen Breakdown](#screen-by-screen-breakdown)
4. [Interactive Components](#interactive-components)
5. [User Flow Diagram](#user-flow-diagram)
6. [Responsive Design](#responsive-design)

---

## Design Philosophy

### Core Principles
- **Industrial Aesthetic**: Retro-technical look inspired by electrical equipment
- **Safety First**: Visual warnings and consequences for mistakes
- **Direct Manipulation**: Click to fix, not multiple choice
- **Progressive Disclosure**: Information revealed as needed
- **Immediate Feedback**: Every action has visual/audio response

### Design Goals
- Create immersive electrician role-play experience
- Make troubleshooting process intuitive and learnable
- Emphasize safety through visual design
- Maintain professional yet engaging atmosphere

---

## Visual Design System

### Color Palette

| Color | Hex Code | Usage | Description |
|-------|----------|-------|-------------|
| **Primary Orange** | `#FF6B35` | Buttons, highlights, warnings | High-energy accent color |
| **Secondary Gold** | `#F7931E` | Secondary actions, text highlights | Complementary warm tone |
| **Dark Navy** | `#1A1A2E` | Main background | Deep, professional base |
| **Darker Navy** | `#0F0F1E` | Background gradient end | Depth and dimension |
| **Light Gray** | `#EAEAEA` | Body text, labels | High readability |
| **Success Green** | `#2ECC71` | Fixed components, success messages | Positive feedback |
| **Danger Red** | `#E74C3C` | Lives lost, errors, tripped breakers | Warning and danger |
| **Warning Gold** | `#F39C12` | Wire nuts, pull chain | Attention-grabbing elements |

### Typography

| Font Family | Usage | Weights | Characteristics |
|-------------|-------|---------|-----------------|
| **Orbitron** | Headers, titles, buttons | 700, 900 | Bold, technical, futuristic |
| **Rajdhani** | Body text, labels, descriptions | 500, 600, 700 | Clean, modern, readable |

**Font Sizes:**
- H1 (Main Title): 64px (responsive: 32px-64px)
- H2 (Screen Titles): 42px
- H3 (Component Names): 24-28px
- Body Text: 18-20px
- Small Text: 14-16px

### Effects & Animations

| Effect | Purpose | Duration | Easing |
|--------|---------|----------|--------|
| Glow/Shadow | Emphasis, active states | N/A | N/A |
| Slide Down | Header entrance | 0.6s | ease-out |
| Fade In | Screen transitions | 0.6s | ease-out |
| Slide Up | Modals appearing | 0.4s | cubic-bezier |
| Spark Explosion | Wrong answer feedback | 0.8s | ease-out |
| Rotate 90° | Close button hover | 0.3s | ease |
| Pulse | Attention indicators | 1.5s | ease-in-out infinite |

---

## Screen-by-Screen Breakdown

### Screen 1: Header (Persistent)

**Always Visible Throughout Game**

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│           ⚡ CEILING FAN TROUBLESHOOTING                    │
│             Interactive Electrical Game                     │
│                                                             │
│        Real Electrician Mode - Find The Problems!          │
│        Always Carry the Right Tools for the Job.           │
│        NO MATTER THE LOAD, WE DO IT BY CODE.               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Visual Elements:**
- **Main Title**: Large (64px), orange glow effect, uppercase, letter-spaced
- **Subtitle**: Gold color, smaller (20px)
- **Mottos**: Two lines below, light gray and orange
- **Background**: Animated grid pattern moving slowly
- **Animation**: Slides down on page load (0.6s)

**Purpose:** Brand identity, sets professional electrician tone, establishes safety theme

---

### Screen 2: Welcome Screen

**Initial Game Screen - Before Difficulty Selection**

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│                   🔧 Welcome, Electrician!                     │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │ 📞 The Call:                                             │ │
│  │ A homeowner's ceiling fan isn't working. You must       │ │
│  │ troubleshoot and find the problem!                       │ │
│  │                                                           │ │
│  │ 🔍 Your Mission:                                         │ │
│  │ The problem is HIDDEN! You must inspect each component  │ │
│  │ to find what's wrong.                                    │ │
│  │                                                           │ │
│  │ ⚠️ Warning:                                              │ │
│  │ Choose carefully! Wrong attempts cost lives and trigger │ │
│  │ dangerous sparks! ⚡                                     │ │
│  │                                                           │ │
│  │ 🔒 Safety First:                                         │ │
│  │ Make sure power is off before attempting to work on     │ │
│  │ problem.                                                 │ │
│  │                                                           │ │
│  │ 🎓 Learn as You Go:                                      │ │
│  │ Each component teaches you electrical safety before     │ │
│  │ you attempt repairs.                                     │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
│                    Select Difficulty:                          │
│                                                                │
│  ┌───────────┐    ┌───────────┐    ┌───────────┐            │
│  │  🟢 EASY  │    │ 🟠 MEDIUM │    │  🔴 HARD  │            │
│  │           │    │           │    │           │            │
│  │ 1 Problem │    │ 2 Problems│    │ 3 Problems│            │
│  │  2 Lives  │    │2 Lives Each│   │2 Lives Each│           │
│  └───────────┘    └───────────┘    └───────────┘            │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Visual Elements:**

1. **Title**: "Welcome, Electrician!" (42px, gold)
2. **Scenario Box**: 
   - Orange-tinted background
   - Orange left border (4px)
   - White text with emoji icons
   - Rounded corners
3. **Difficulty Buttons**:
   - Easy: Green gradient background
   - Medium: Orange gradient background
   - Hard: Red gradient background
   - Large (24px font), uppercase
   - Hover: Lift up 5px, glow shadow
   - Click animation: Ripple effect

**Purpose:** Set the scenario, explain rules, emphasize safety, allow difficulty selection

**User Actions:** Click one of three difficulty buttons

---

### Screen 3: Main Game Screen

**Active Troubleshooting Interface**

```
┌────────────────────────────────────────────────────────────────┐
│  ┌──────────────┐  ┌──────────────────┐  ┌─────────────────┐  │
│  │  Difficulty  │  │ Lives (Problem)  │  │ Problems Fixed  │  │
│  │     EASY     │  │      ❤️❤️        │  │      0 / 1      │  │
│  └──────────────┘  └──────────────────┘  └─────────────────┘  │
│                                                                │
│  ┌──────────────────┐           ┌──────────────────┐         │
│  │                  │           │                  │         │
│  │       🌀        │           │       🔌        │         │
│  │                  │           │                  │         │
│  │  CEILING FAN    │           │  JUNCTION BOX   │         │
│  │                  │           │                  │         │
│  │ Click to inspect │           │ Click to inspect │         │
│  └──────────────────┘           └──────────────────┘         │
│                                                                │
│  ┌──────────────────┐           ┌──────────────────┐         │
│  │                  │           │                  │         │
│  │       💡        │           │       ⚡        │         │
│  │                  │           │                  │         │
│  │  WALL SWITCH    │           │ CIRCUIT BREAKER │         │
│  │                  │           │                  │         │
│  │ Click to inspect │           │ Click to inspect │         │
│  └──────────────────┘           └──────────────────┘         │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Visual Elements:**

1. **Info Cards** (Top Row):
   - Dark background with orange border
   - Label (14px, uppercase, gold)
   - Value (32px, white, Orbitron font)
   - Lives display: Heart emojis
   - Drop shadow

2. **Component Cards** (2x2 Grid):
   - Large square cards
   - Dark gradient background
   - Orange border (default)
   - Large emoji icon (80px)
   - Component name (24px, orange, uppercase)
   - Status text (16px, gold)
   - Hover: Lift up 10px, scale 1.02, brighter border, orange glow
   - Cursor: pointer
   - Transition: 0.4s ease

3. **Fixed Component State**:
   - Border changes to green
   - Background has green tint
   - Name text changes to green
   - Status: "✅ FIXED!"
   - No longer clickable

**Purpose:** Main gameplay interface, component selection, progress tracking

**User Actions:** Click any component card to inspect it

---

### Screen 4: Educational Modal

**First Modal - Learning Phase**

```
┌────────────────────────────────────────────────────────────────┐
│ ┌────────────────────────────────────────────────────────────┐ │
│ │ ┌──────────────────────────────────────────────────────┐   │ │
│ │ │  💡 Wall Switch                               [X]    │   │ │
│ │ └──────────────────────────────────────────────────────┘   │ │
│ │                                                            │ │
│ │  ┌────────────────────────────────────────────────────┐   │ │
│ │  │ ⚠️ Safety First: Always check the wall switch    │   │ │
│ │  │ first! The wall switch controls power flow to the  │   │ │
│ │  │ ceiling fan. If it's in the OFF position, no       │   │ │
│ │  │ electricity reaches the fan. Switches are simple   │   │ │
│ │  │ mechanical devices that complete or break the      │   │ │
│ │  │ electrical circuit.                                │   │ │
│ │  └────────────────────────────────────────────────────┘   │ │
│ │                                                            │ │
│ │              ┌─────────────────────────┐                  │ │
│ │              │  Attempt Repair →       │                  │ │
│ │              └─────────────────────────┘                  │ │
│ │                                                            │ │
│ └────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────┘
```

**Visual Elements:**

1. **Modal Overlay**: 
   - Full screen
   - 95% black background
   - Blur effect

2. **Modal Container**:
   - Dark gradient background
   - Orange border (3px)
   - Rounded corners (20px)
   - Max-width: 800px
   - Centered on screen
   - Slide-up animation (0.4s)

3. **Header**:
   - Orange-to-gold gradient background
   - White text (28px, Orbitron)
   - Component emoji + name
   - Close button [X]: 36px, rotates on hover

4. **Educational Box**:
   - Orange-tinted background
   - Orange left border (4px)
   - White text (18px)
   - Line height: 1.8
   - Rounded corners

5. **Continue Button**:
   - Green gradient background
   - White text (20px, Orbitron, bold)
   - Large padding (20px × 50px)
   - Centered
   - Hover: Lift up, green glow

**Purpose:** Teach about component before allowing repair attempt

**User Actions:** 
- Click "Attempt Repair →" to proceed
- Click [X] to close and try different component

---

### Screen 5: Interactive Fix Modal - Wall Switch

**Second Modal - Hands-On Repair**

```
┌────────────────────────────────────────────────────────────────┐
│ ┌────────────────────────────────────────────────────────────┐ │
│ │ ┌──────────────────────────────────────────────────────┐   │ │
│ │ │  💡 Wall Switch                               [X]    │   │ │
│ │ └──────────────────────────────────────────────────────┘   │ │
│ │                                                            │ │
│ │     Try fixing this component. Click the switch to flip it!│ │
│ │                                                            │ │
│ │                    ┌───────────┐                          │ │
│ │                    │           │                          │ │
│ │                    │     ╱     │  ← Switch Toggle         │ │
│ │                    │           │     (Click Me!)          │ │
│ │                    │           │                          │ │
│ │                    └───────────┘                          │ │
│ │                  Wall Switch Plate                        │ │
│ │                                                            │ │
│ └────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────┘

IF CORRECT (Switch IS the problem):
  - Toggle flips UP with animation
  - Changes to GREEN with glow
  - Modal closes after 0.8s
  - "✅ CORRECT! Problem FIXED!" message

IF WRONG (Switch is NOT the problem):
  - ⚡ SPARKS EXPLODE from center!
  - Electric "BZZZZT!" sound
  - Modal closes
  - "⚡ YOU DIDN'T TURN OFF THE POWER! Wrong component! Lives: 1"
```

**Visual Elements:**

1. **Instruction Text**:
   - Gold color (22px)
   - Centered
   - Bold

2. **Switch Plate**:
   - Gray gradient (realistic look)
   - 120px × 180px
   - Rounded corners
   - Shadow depth
   - Centered

3. **Switch Toggle**:
   - Initially: Angled DOWN-left (-15°), gray
   - Clickable (cursor: pointer)
   - 50px × 70px
   - Transition: 0.4s

4. **After Click (Correct)**:
   - Rotates UP-right (+15°)
   - Changes to green gradient
   - Glowing green shadow (30px radius)

**Purpose:** Interactive repair - player directly manipulates switch

**User Actions:** Click the switch toggle

---

### Screen 6: Interactive Fix Modal - Circuit Breaker

**Breaker Panel Interface**

```
┌────────────────────────────────────────────────────────────────┐
│ ┌────────────────────────────────────────────────────────────┐ │
│ │ ┌──────────────────────────────────────────────────────┐   │ │
│ │ │  ⚡ Circuit Breaker Panel                     [X]    │   │ │
│ │ └──────────────────────────────────────────────────────┘   │ │
│ │                                                            │ │
│ │  Try fixing this component. Click the BEDROOM breaker!    │ │
│ │                                                            │ │
│ │               ┌─────────────────────┐                     │ │
│ │               │   MAIN PANEL        │                     │ │
│ │               ├─────────────────────┤                     │ │
│ │               │ ┌────┐    ┌────┐   │                     │ │
│ │               │ │ ✓  │    │ ✗  │ ← BEDROOM (Red/Tripped)│ │
│ │               │ │Kitchen│  │Bedroom││                    │ │
│ │               │ └────┘    └────┘   │  (Click to reset!)  │ │
│ │               │                     │                     │ │
│ │               │ ┌────┐    ┌────┐   │                     │ │
│ │               │ │ ✓  │    │ ✓  │   │                     │ │
│ │               │ │Bath │    │Living│ │                    │ │
│ │               │ └────┘    └────┘   │                     │ │
│ │               └─────────────────────┘                     │ │
│ │                                                            │ │
│ └────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────┘

Breaker States:
✓ (Green) = ON - Working normally
✗ (Red) = TRIPPED - Click to reset!

IF CORRECT:
  - Red breaker flips to GREEN
  - Glowing green effect
  - Success!

IF WRONG:
  - ⚡ SPARKS!
  - Sound effect
  - Lose life
```

**Visual Elements:**

1. **Breaker Panel**:
   - Gray metallic gradient
   - Dark border (4px)
   - 240px × 300px
   - Realistic panel look

2. **Panel Title**:
   - "MAIN PANEL" text
   - White, 16px, centered

3. **Breaker Grid**:
   - 2×2 layout
   - Each breaker: 60px height
   - Gap between: 15px

4. **Individual Breakers**:
   - OFF (Red): Red gradient, pulsing animation
   - ON (Green): Green gradient, subtle glow
   - Border: Dark (2px)
   - Rounded corners
   - Labels below: "Kitchen", "Bedroom", "Bath", "Living"
   - Cursor: pointer

5. **Bedroom Breaker** (The Problem):
   - Initially RED
   - Pulsing animation (draws attention)
   - Labeled clearly

**Purpose:** Show realistic breaker panel, player resets tripped breaker

**User Actions:** Click red bedroom breaker

---

### Screen 7: Interactive Fix Modal - Junction Box

**Wire Repair Interface**

```
┌────────────────────────────────────────────────────────────────┐
│ ┌────────────────────────────────────────────────────────────┐ │
│ │ ┌──────────────────────────────────────────────────────┐   │ │
│ │ │  🔌 Junction Box                              [X]    │   │ │
│ │ └──────────────────────────────────────────────────────┘   │ │
│ │                                                            │ │
│ │  Look for wire(s) with visible GAPS! Click the broken     │ │
│ │  wire(s) to reconnect them!                               │ │
│ │                                                            │ │
│ │               ┌─────────────────────┐                     │ │
│ │               │ •              •    │  ← Screw           │ │
│ │               │                     │                     │ │
│ │               │  ═══  •  ═══      │  ← RED Wire (GAP!)  │ │
│ │               │                     │     Click to fix!   │ │
│ │               │  ═══════════       │  ← BLACK (Intact)   │ │
│ │               │                     │     Don't touch     │ │
│ │               │  ═══════════       │  ← WHITE (Intact)   │ │
│ │               │                     │                     │ │
│ │               │ •              •    │                     │ │
│ │               └─────────────────────┘                     │ │
│ │                   Junction Box                            │ │
│ │                                                            │ │
│ └────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────┘

Wire States:
═══════════  = INTACT (connected, don't touch)
═══  •  ═══  = BROKEN (gap visible, click to fix!)
═══🟠═══    = CONNECTED (wire nut appears, glows)

IF CORRECT:
  - Click broken wire(s)
  - Segments slide together
  - Orange wire nut appears
  - Wire glows
  - When all broken wires fixed: Success!

IF WRONG:
  - ⚡ SPARKS!
  - Lose life
```

**Visual Elements:**

1. **Junction Box**:
   - Gray metallic gradient
   - Dark border (4px)
   - 220px × 220px
   - 4 screws in corners (small circles)

2. **Wire Container**:
   - Centered inside box
   - 3 wires stacked vertically

3. **Intact Wire**:
   - Single continuous bar
   - 100px wide, 6px tall
   - Colored (red/black/white-gray)
   - NOT clickable

4. **Broken Wire** (The Problem):
   - TWO segments with GAP
   - Left segment: 45px
   - Right segment: 45px
   - Gap: 10px visible space
   - Pulsing golden indicator (●) in gap
   - Cursor: pointer
   - Hover: Brightness increases

5. **After Click (Connected)**:
   - Segments slide together (0.4s animation)
   - Orange circle (wire nut) appears on right end
   - Wire nut pops in (scale animation)
   - Entire wire glows (matches wire color)

6. **Randomization**:
   - Each game: 1-2 wires randomly broken
   - Can be any combination: red, black, white

**Purpose:** Most complex repair - shows realistic wire problem with visual diagnosis

**User Actions:** Click only the broken wire(s) with gaps

---

### Screen 8: Interactive Fix Modal - Ceiling Fan

**Pull Chain Interface**

```
┌────────────────────────────────────────────────────────────────┐
│ ┌────────────────────────────────────────────────────────────┐ │
│ │ ┌──────────────────────────────────────────────────────┐   │ │
│ │ │  🌀 Ceiling Fan                               [X]    │   │ │
│ │ └──────────────────────────────────────────────────────┘   │ │
│ │                                                            │ │
│ │     Try fixing this component. Click the pull chain!      │ │
│ │                                                            │ │
│ │                     ─────────                             │ │
│ │                    /         \                            │ │
│ │               ─────   [●]   ─────  ← Fan Blades          │ │
│ │                    \         /       (Not spinning)       │ │
│ │                     ─────────                             │ │
│ │                                                            │ │
│ │                         |  ← Chain                        │ │
│ │                         |                                 │ │
│ │                        [🟡] ← Pull (Click!)              │ │
│ │                                                            │ │
│ └────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────┘

IF CORRECT:
  - Chain animates DOWN briefly
  - Fan blades begin SPINNING
  - Smooth rotation animation
  - Success!

IF WRONG:
  - ⚡ SPARKS!
  - Lose life
```

**Visual Elements:**

1. **Fan Assembly**:
   - 5 brown blades radiating from center
   - Motor housing (gray circle in center)
   - 250px × 250px total
   - Positioned top-center

2. **Fan Blades**:
   - Each: 140px × 45px
   - Brown gradient
   - Rounded ends
   - 72° apart (360° / 5 blades)
   - Initially: Static

3. **Pull Chain**:
   - Gray vertical line (4px × 70px)
   - Extends down from motor
   - Gold bead/handle at bottom (24px × 30px)
   - Cursor: pointer
   - Hover: Scale 1.1, golden glow

4. **After Click (Correct)**:
   - Pull animation: Chain pulls down 15px, bounces back
   - Blades: Start rotating
   - Rotation: 2s per revolution, linear, infinite
   - Smooth continuous spin

**Purpose:** Simple but satisfying - pull chain to activate fan

**User Actions:** Click golden pull chain handle

---

### Screen 9: Spark Effect

**Wrong Component Feedback**

```
        ⚡ ✦ ⚡
    ✦         ✦
  ⚡             ⚡
✦                 ✦
⚡    DANGER!     ⚡
✦                 ✦
  ⚡             ⚡
    ✦         ✦
        ⚡ ✦ ⚡

20 particles exploding outward
Golden yellow color (#FFD700)
Glowing effect
0.8 second duration
"BZZZZT!" sound effect
```

**Visual Elements:**

1. **Spark Particles**:
   - 20 small circles (10px)
   - Golden yellow (#FFD700)
   - Golden glow/shadow (20px radius)
   - Start: Center of screen
   - Animation: Fly outward in all directions
   - Distance: 100-250px (randomized)
   - Fade out as they fly
   - Scale down to 0

2. **Sound Effect**:
   - Electric zap/discharge sound
   - Generated via Web Audio API
   - Sawtooth wave
   - Frequency: 200Hz → 50Hz (drops)
   - Duration: 0.3s
   - Volume: 0.3

3. **Timing**:
   - Triggered immediately on wrong component
   - Particles appear and fly (0.8s)
   - Auto-remove after animation

**Purpose:** Dramatic negative feedback representing electrical shock/danger

**Triggers:** Wrong component selected

---

### Screen 10: Success Message

**Floating Toast Notification - Correct Fix**

```
┌────────────────────────────────┐
│  ✅ CORRECT! Problem FIXED!   │
└────────────────────────────────┘
  ↑ Slides in from right
  Green background
  White text
  Auto-disappears after 3s
```

**Visual Elements:**

1. **Message Box**:
   - Green gradient background
   - White border (2px)
   - Rounded corners (15px)
   - Padding: 25px × 40px
   - Shadow: Strong depth

2. **Text**:
   - White, bold (18px)
   - Checkmark emoji

3. **Animation**:
   - Slides in from right (0.4s)
   - Stays 2.6s
   - Fades out (0.4s)
   - Position: Fixed top-right corner

**Purpose:** Positive reinforcement for correct diagnosis

---

### Screen 11: Error Message

**Floating Toast Notification - Wrong Fix**

```
┌───────────────────────────────────────────────┐
│  ⚡ YOU DIDN'T TURN OFF THE POWER!          │
│  Wrong component! Lives: 1                   │
└───────────────────────────────────────────────┘
  ↑ Slides in from right
  Red background
  White text
  Auto-disappears after 3s
```

**Visual Elements:**

1. **Message Box**:
   - Red gradient background
   - Red border (2px)
   - Rounded corners (15px)
   - Padding: 25px × 40px
   - Shadow: Strong depth

2. **Text**:
   - White, bold (18px)
   - Lightning emoji
   - Two lines (message + lives remaining)

3. **Animation**:
   - Slides in from right (0.4s)
   - Stays 2.6s
   - Fades out (0.4s)
   - Position: Fixed top-right corner

**Purpose:** Safety-themed negative feedback, shows remaining lives

---

### Screen 12: Win Screen

**Victory Display**

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│                       🎉 SUCCESS!                              │
│                    (Bouncing animation)                        │
│                                                                │
│         You fixed all the problems! The fan is                │
│                working perfectly!                              │
│                                                                │
│                   ┌─────────────────┐                         │
│                   │   Play Again    │                         │
│                   └─────────────────┘                         │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Visual Elements:**

1. **Title**: 
   - "🎉 SUCCESS!" (64px, Orbitron, green)
   - Green text shadow/glow
   - Bounce animation (infinite)

2. **Message**:
   - White text (24px)
   - Centered
   - Line spacing: 1.6

3. **Play Again Button**:
   - Orange gradient background
   - Orange border (3px)
   - White text (20px, Orbitron, bold)
   - Large padding
   - Hover: Lift up, orange glow
   - Refreshes page on click

**Purpose:** Celebrate success, offer replay

**User Actions:** Click "Play Again"

---

### Screen 13: Lose Screen

**Game Over Display**

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│                     💥 GAME OVER!                              │
│                                                                │
│               You ran out of lives!                           │
│            Better luck next time, electrician.                │
│                                                                │
│                   ┌─────────────────┐                         │
│                   │   Try Again     │                         │
│                   └─────────────────┘                         │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Visual Elements:**

1. **Title**: 
   - "💥 GAME OVER!" (64px, Orbitron, red)
   - Red text shadow/glow

2. **Message**:
   - White text (24px)
   - Centered
   - Sympathetic tone

3. **Try Again Button**:
   - Orange gradient background
   - Orange border (3px)
   - White text (20px, Orbitron, bold)
   - Large padding
   - Hover: Lift up, orange glow
   - Refreshes page on click

**Purpose:** Encourage retry after failure

**User Actions:** Click "Try Again"

---

## Interactive Components

### Component States

#### Default State
- Border: Orange (3px)
- Background: Dark gradient
- Icon: Normal size (80px)
- Name: Orange text
- Status: "Click to inspect"
- Cursor: Pointer
- Hover: Available

#### Hover State
- Transform: translateY(-10px) scale(1.02)
- Border: Brighter orange with glow
- Box-shadow: 0 20px 50px rgba(255, 107, 53, 0.3)
- Transition: 0.4s ease

#### Fixed State
- Border: Green (3px)
- Background: Dark gradient with green tint
- Name: Green text
- Status: "✅ FIXED!"
- Cursor: Default (not clickable)
- No hover effect

---

## User Flow Diagram

```
┌─────────────┐
│   START     │
│   (Load)    │
└──────┬──────┘
       │
       ▼
┌─────────────────────┐
│  Welcome Screen     │
│  Read Scenario      │
│  View Safety Rules  │
└──────┬──────────────┘
       │
       ▼
┌─────────────────────┐
│ Select Difficulty   │
│ • Easy (1 problem)  │
│ • Medium (2)        │
│ • Hard (3)          │
└──────┬──────────────┘
       │
       ▼
┌─────────────────────┐
│  Main Game Screen   │
│  4 Components       │
│  Progress Display   │
└──────┬──────────────┘
       │
       ▼
┌─────────────────────┐
│  Click Component    │
│  (Player Choice)    │
└──────┬──────────────┘
       │
       ▼
┌─────────────────────┐
│ Educational Modal   │
│ Learn About It      │
└──────┬──────────────┘
       │
       ▼
┌─────────────────────┐
│ Interactive Fix     │
│ Physical Repair     │
└──────┬──────────────┘
       │
       ├─► CORRECT? ─────┐
       │                  │
       │                  ▼
       │          ┌─────────────┐
       │          │ Fix Applied │
       │          │ Lives Reset │
       │          │ Progress++  │
       │          └──────┬──────┘
       │                  │
       │                  ├─► All Fixed? ──► WIN SCREEN ──► Play Again?
       │                  │
       │                  └─► More Problems ──┐
       │                                       │
       │                  ┌────────────────────┘
       │                  │
       │                  ▼
       │          Back to Main Screen
       │
       └─► WRONG? ──────┐
                         │
                         ▼
                 ┌─────────────┐
                 │ ⚡ SPARKS!  │
                 │ Lose Life   │
                 └──────┬──────┘
                         │
                         ├─► Lives > 0? ──► Try Again (Main Screen)
                         │
                         └─► Lives = 0? ──► LOSE SCREEN ──► Try Again?
```

---

## Responsive Design

### Breakpoints

| Screen Size | Max Width | Grid Columns | Font Adjustments |
|-------------|-----------|--------------|------------------|
| Mobile | 480px | 1 column | H1: 32px, smaller spacing |
| Tablet | 768px | 2 columns | H1: 48px, reduced padding |
| Desktop | 1200px+ | 2 columns | H1: 64px, full spacing |

### Mobile Optimizations
- Components stack vertically on small screens
- Touch-friendly hit areas (minimum 44px × 44px)
- Modal width: 95% on mobile
- Font sizes scale down proportionally
- Reduced animation complexity for performance

---

## Accessibility Considerations

### Color Contrast
- All text meets WCAG AA standards (4.5:1 minimum)
- Critical information not conveyed by color alone
- Multiple feedback methods (visual + text + sound)

### Keyboard Navigation
- All interactive elements keyboard accessible
- Tab order follows logical flow
- Escape key closes modals

### Screen Readers
- Semantic HTML structure
- Alt text for visual elements
- ARIA labels where appropriate

---

## Performance Optimizations

### Animations
- CSS-based animations (hardware accelerated)
- Transform and opacity (no layout thrashing)
- Reduced motion for accessibility preferences

### Assets
- Single HTML file (no external dependencies)
- Embedded CSS and JavaScript
- SVG/emoji icons (no image files)
- Web Audio API (no sound file downloads)

---

## Design Rationale

### Why This Visual Style?

**Retro-Industrial Aesthetic:**
- Reflects real electrical equipment and control panels
- Creates professional, technical atmosphere
- Distinguishes from generic educational games

**Orange/Gold Color Scheme:**
- High visibility and attention-grabbing
- Associated with caution/electrical work
- Energetic and engaging

**Dark Background:**
- Reduces eye strain for extended play
- Makes colored elements pop
- Modern, professional appearance

**Orbitron Font:**
- Technical, futuristic feel
- Excellent readability at large sizes
- Reinforces electrician/technical theme

**Direct Manipulation:**
- More engaging than multiple choice
- Builds muscle memory
- Feels like real troubleshooting work

---

**Document Version:** 1.0  
**Last Updated:** December 2024  
**Total Screens:** 13  
**Interactive Elements:** 25+  
**Animation Effects:** 20+
