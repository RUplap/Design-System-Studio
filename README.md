# Factory Floor DS Studio

**A node-based studio for building and testing a design system for industrial monitoring software.**

[**▶ Open the live demo**](https://YOUR-USERNAME.github.io/factory-floor-ds-studio/)

<!-- Add a screenshot: save it as screenshot.png in this folder, then remove the comment marks below -->
<!-- ![Factory Floor DS Studio — node canvas](screenshot.png) -->

---

## The problem

In factory software, design mistakes have real consequences. If an alert is labeled "critical" when it isn't, operators learn to ignore it. If a status shows up only as an amber dot, someone will miss it. Most design systems keep their rules in a static doc that people check after the design is done, if they check at all.

I wanted to see what happens when those rules run *while* you design.

## What it is

The Studio lets you build UI the same way the design system is structured:

```
Tokens  →  Components  →  Factory screens  →  AI review  →  Preview + approve
```

Every step is a node on a canvas. The wires show how a color, type style or label travels all the way into a finished screen. Change a token and everything downstream updates.

## What you can do

**Build on a node canvas.** Connect color, type, label and theme tokens to a component, then drop that component into a full screen.

**Preview real screens.** There are four templates, each in light and dark mode:
- AI factory dashboard
- Floor map + device diagnostics
- Predictive health panel
- Maintenance copilot

**Get reviewed by agents.** Wire any component into an agent node and it audits the design:

| Agent | What it checks |
|---|---|
| Accessibility | Contrast, 44px touch targets, accessible names, focus rings |
| Severity | "Critical" is only used for failures that actually stop work |
| Status meaning | Green, amber and red always mean operational state and never appear without a label |
| Label copy | Button and alert wording |

**Fix in one click.** Every failed check explains the problem in plain language and offers a fix, like *"Swap fill to interactive-hover"* or *"Show state label."* You choose which fixes to apply.

**Browse the system.** The Design system view documents every token, contrast ratio, component spec and do/don't rule.

**Save your work.** Create, rename, import and export graphs from the Files view.

## Two roles for AI

The Studio is also an experiment in how AI fits into a design workflow. You can switch between two modes, or run both at once:

- **AI as a node.** The agent is a reviewer you wire into the pipeline on purpose. You decide where it looks and what it sees.
- **AI as a builder.** A chat assistant edits the graph for you: *"fix all," "dark theme," "add agent."*

Putting the two side by side shows the trade-off clearly. The node is transparent and you stay in control. The builder is faster but harder to follow. In both modes, the work ends at a Preview node where a person signs off. You can't approve without an AI report wired in, and any later edit resets the approval.

## Design decisions

- **Status colors are reserved.** Green, amber and red only describe operational state. Device type gets names, icons and neutral labels instead.
- **Color never stands alone.** Every status comes with a word, an icon or a number.
- **44px minimum targets.** Operators may be wearing gloves or working on a tablet on the floor.
- **Contrast is measured, not guessed.** Every token shows its real WCAG ratio, including the ones that fail. (Amber on white is 2.15:1, so it's only used as a fill and never as text.)
- **Severity matches impact.** "Critical" means it blocks operation or safety. Everything else is a warning.

## How it's built

- One self-contained HTML file using vanilla JavaScript, with no framework and no build step
- Type: Outfit (headings), Geist (body), Geist Mono (device IDs and data)
- Tokens: Factory Floor DS v1.4.0
- The agents are rule-based checks that run in the browser. There are no API calls and no keys needed.
- Graphs save to your browser's local storage

## Run it locally

Download the repo and open `index.html` in a browser. That's all you need.

## About

Designed and built by **Rohan Uplap**, a UX product designer with 16+ years of experience exploring how to design AI products, and how AI can change the design process itself.

[LinkedIn](https://www.linkedin.com/in/rohanuplap) · [SpaceUX](https://spaceux.online)

All device names, data and scenarios are fictional.

## License

MIT. See [LICENSE](LICENSE).
