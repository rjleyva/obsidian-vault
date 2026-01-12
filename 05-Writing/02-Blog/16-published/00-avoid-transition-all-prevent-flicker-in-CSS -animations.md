---
title: "Avoid transition: all: Prevent Flicker in CSS Animations"
description: It wasn’t catastrophic but once you see it, you can’t unsee it. On slower machines or reduced motion environments, it became even more noticeable.
created: 2025-12-04
updated: 2026-01-04
tags:
  - css
  - debugging
  - transitions
  - pitfalls
  - best-practices
  - performance
  - accessibility
  - frontend-development
---

Hi it's RJ, and today I want to share about the risk of `transition: all` in CSS.

## The Symptom

While implementing a dark mode toggle, I ran into a small but surprisingly distracting visual issue. During the theme transition, the social media icons on the page would briefly flash before settling into their correct color, while the rest of the UI transitioned smoothly.

At first, the behavior pointed to something more complex: a hydration mismatch, a delayed theme state update, or possibly an SVG rendering quirk. After spending more time than I care to admit inspecting React DevTools and revisiting theme logic, the true cause turned out to be far simpler.

## The Root Cause

The issue wasn’t React, the theme toggle, or the build setup. It was a single line of CSS:

```css
transition: all;
```

The social icons were styled using the `filter` property for color adjustments. By declaring `transition: all`, the browser was instructed to animate _every_ animatable property whenever a change occurred.

During the theme switch, this caused certain properties—particularly `filter`—to pass through intermediate or invalid visual states. The result was a brief flicker as the browser attempted to interpolate values that were never meant to be animated together.

## The FIX

Once the problem was clear, the solution was straightforward: scope the transition to only the property that actually needed animation.

Here’s the updated CSS:

```css
.socials__icon {
  /* Transition only filter to prevent unwanted flickers */
  transition: filter var(--transition-duration-normal);
  filter: drop-shadow(0 0 0 transparent);
}
```

In practical terms, this meant replacing:

```css
transition: all;
```

with:

```css
transition: filter;
```

The result was immediate and definitive. The flicker disappeared entirely.

- No JavaScript changes
- No theme logic updates
- No framework-level debugging

Just a properly scoped transition.

## A Lesson in transition: all

> `transition: all` is convenient — but often dangerous.

While it’s tempting to use `transition: all` for speed and simplicity, it can easily introduce unintended side effects. Animating every possible property can:

- Trigger unexpected visual glitches during state changes
- Produce strange intermediate render states
- Make UI bugs harder to diagnose and reason about

Explicitly defining which properties should transition leads to safer, more predictable behavior—and avoids subtle regressions that can slip past code review.

This issue was a good reminder that not all bugs stem from complex logic or architectural decisions. Sometimes, a single careless line of CSS is enough to create a disproportionately frustrating problem.

## Key Takeaway

Be intentional with your transitions. Animate only the properties you actually need, and avoid `transition: all` unless you truly mean it. Small details like this can make the difference between a polished UI and one plagued by subtle visual inconsistencies.

---
