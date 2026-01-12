---
title: How I Set Up WezTerm for Distraction-Free Coding
description: How visual noise in my terminal was quietly sabotaging long coding sessions, and the minimal changes that transformed it into a focused workspace.
tags:
  - wezterm
  - terminal
  - setup
  - zen-mode
  - productivity
  - focus
  - minimalism
  - ergonomics
created: 2025-12-05
updated: 2026-01-04
---

Hi it's RJ, and today I want to share the reason behind my new WezTerm terminal setup.

> This isn’t a “best practices” guide. It’s just what works for me.

## The Problem

During long coding sessions, I noticed something was off. My terminal felt like it was fighting for my attention—subtle visual elements that seemed harmless were quietly draining my focus. By the end of the day, I was more exhausted than the work warranted.

At first, I chalked it up to general fatigue or screen time. But the pattern was too consistent—8-hour sessions left me mentally drained in ways that shorter, more intense work never did.

## The Investigation

I started paying closer attention to what was actually on my screen during these sessions. The tab bar was always there, even though I used TMUX for window management. Window chrome added unnecessary visual weight. Even the background had a slight translucency that made text feel less solid.

These weren't catastrophic issues individually, but collectively they created a low-level cognitive load that accumulated throughout the day.

## The Source

The problem wasn't with any single feature—it was that terminal defaults are optimized for discoverability and features, not for sustained focus. Modern terminals come loaded with UI elements designed to help users explore and manage multiple contexts, but when you're deep in code, these become distractions.

My terminal was a tool I was constantly aware of, rather than one that faded into the background.

## The Solution

The solution was surprisingly simple: strip the terminal down to only what serves focus and ergonomics.

Here's what I changed:

**Before: Feature-rich but distracting**

```lua
enable_tab_bar = true  -- Always visible, even when unused
window_decorations = "TITLE|RESIZE|CLOSE|MINIMIZE"  -- Full chrome
window_background_opacity = 0.85, -- Slight transparency
macos_window_background_blur = 8,
scrollback_lines = 1000  -- Too limited for long sessions
```

**After: Minimal but practical**

```lua
enable_tab_bar = false  -- I'm using TMUX
window_decorations = "RESIZE"  -- Just enough to resize when needed
window_background_opacity = 1.0  -- Full opacity
macos_window_background_blur = 10  -- Subtle separation without fuzziness
scrollback_lines = 10000  -- Deep buffer for reviewing long outputs
font = wezterm.font_with_fallback({ "Lilex Nerd Font" })
font_size = 18  -- Comfort over cramming
```

The colors followed the same principle—[solarized-osaka](https://github.com/craftzdog/solarized-osaka.nvim) for long sessions, prioritizing eye comfort over visual flair.

## A Lesson in Terminal Design

> Small visual adjustments compound in impact.

What I learned is that tools optimized for exploration aren't necessarily optimized for creation. When you're building, you want your environment to be as invisible as possible.

This wasn't about creating the "perfect" terminal setup—it was about removing the friction that was preventing deep, sustained work. Each tweak served the same goal: making the terminal disappear so the code could take center stage.

## Key Takeaway

Be intentional about your development environment. Every pixel on your screen during 8-hour coding sessions matters. What seems like a minor UI preference can be the difference between a productive day and one spent wrestling with your tools instead of your code.

The most effective optimizations often aren't the flashy ones—they're the quiet subtractions that reduce cognitive load.

## The Full Zen Configuration

```lua
local wezterm = require("wezterm")

local M = {}

M.spec = {
  enable_tab_bar = false,
  window_decorations = "RESIZE",
  window_background_opacity = 1.0,
  macos_window_background_blur = 10,
  font = wezterm.font_with_fallback({ "Lilex Nerd Font" }),
  font_size = 18,
  scrollback_lines = 10000,

  colors = {
    foreground = "#839395",
    background = "#001419",

    cursor_bg = "#839395",
    cursor_border = "#839395",
    cursor_fg = "#001419",

    selection_bg = "#1a6397",
    selection_fg = "#839395",

    ansi = {
      "#001014",
      "#db302d",
      "#849900",
      "#b28500",
      "#268bd3",
      "#d23681",
      "#29a298",
      "#9eabac",
    },

    brights = {
      "#001419",
      "#db302d",
      "#849900",
      "#b28500",
      "#268bd3",
      "#d23681",
      "#29a298",
      "#839395",
    },
  },
}

return M.spec
```

Over time, I realized that small adjustments—fonts, colors, scrollback, even
subtle blur—compound in impact. Each tweak reduces friction, letting the terminal
fade into the background so I can focus on code.

This setup is my "zen mode." It's not perfect and it will probably evolve, but
for now, it transforms the terminal from a tool I wrestle with into a space I can
inhabit for hours, fully immersed in work.
