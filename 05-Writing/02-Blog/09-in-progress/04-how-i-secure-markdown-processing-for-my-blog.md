---
title: How I Secure Markdown Processing for My Blog
description: A deep dive into my restrictive markdown sanitization approach that prioritizes security while maintaining rich content features, exploring the trade-offs and implementation details.
tags:
  - security
  - markdown
  - web-development
  - sanitization
  - content-security
  - unified
  - rehype
  - content-processing
created: 2025-12-27
updated: 2026-01-04
---

Hi it's RJ, and today I want to share about my markdown processing security approach that went from "good enough" to military-grade paranoia.

## The Problem

While building my blog's content pipeline, I started getting uncomfortable with how permissive most markdown processors are. They allow HTML, trust content sources, and rely on complex sanitization libraries to clean up after the fact. I knew this wasn't right for my use case—especially since I wanted to write about security topics.

The more I thought about it, the more I realized how dangerous content processing can be. Markdown itself is safe, but converting it to HTML opens up attack vectors like XSS, data exfiltration, and content injection. Even though I write all my own content, I wanted defense in depth.

## The Investigation

I spent time researching markdown security and was surprised by what I found. Most processors use libraries like DOMPurify or sanitize-html that work by pattern matching—trying to identify and remove dangerous content. But this approach always felt reactive to me.

What if a new attack pattern emerged? What if there was a bypass technique I hadn't considered? The uncertainty bothered me. I wanted something more predictable, something where I could know exactly what was allowed rather than hoping the bad stuff got caught.

## The Root Cause

The issue wasn't with any specific library—it was the fundamental approach. Permissive sanitization relies on staying one step ahead of attackers, while deny-all approaches eliminate entire classes of vulnerabilities by default.

I realized most markdown processors prioritize features over security, allowing images, iframes, scripts, and complex HTML. But for my blog, I didn't need any of that. I wanted text content with code examples, and I wanted it to be bulletproof.

## The FIX

The solution was surprisingly simple: deny everything by default, allow only what's explicitly safe. Here's the aggressive sanitization configuration I landed on:

```typescript
{
  // Allow only safe HTML elements and attributes
  allowDoctypes: false,
  allowComments: false,

  // Strip dangerous attributes - be very restrictive
  attributes: {
    '*': ['className', 'id', 'lang'],
    a: ['href', 'title', 'rel'],
    code: ['className'],
    pre: ['className'],
    h1: ['id'],
    h2: ['id'],
    h3: ['id'],
    h4: ['id'],
    h5: ['id'],
    h6: ['id']
  },

  // Allow only safe elements (no images, iframes, etc.)
  tagNames: [
    'p', 'div', 'span', 'br', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6',
    'ul', 'ol', 'li', 'blockquote', 'pre', 'code', 'strong', 'em',
    'del', 'a', 'hr', 'table', 'thead', 'tbody', 'tr', 'th', 'td'
  ],

  // Strip all protocols except safe ones
  protocols: {
    href: ['http', 'https', 'mailto']
  },

  // Strip any content that looks like HTML with dangerous attributes
  strip: [
    'script', 'style', 'iframe', 'object', 'embed', 'form', 'input',
    'img'
  ]
}
```

This strips everything dangerous: scripts, styles, images, forms, iframes. Links can only use safe protocols. Even attributes are heavily restricted—no onclick, onload, or data-\* attributes.

## A Lesson in Security-First Development

> Security isn't about features—it's about constraints that prevent disasters.

What I learned is that defensive programming requires being uncomfortable. Most markdown processors are designed for convenience, but when security matters, you need to work within strict boundaries. This approach eliminates entire attack surfaces rather than trying to patch them.

The whitelist mentality changes everything. Instead of wondering "what dangerous content might slip through?", I know exactly what can appear in my content. No surprises, no edge cases.

## Key Takeaway

If you're building content systems that need to prioritize security, especially with user-generated content, the deny-all approach is worth considering. It might feel restrictive at first, but the peace of mind is invaluable.

For my use case, the trade-offs work perfectly. I focus on text and code, so I don't need images or embedded content anyway. When I do need rich media, I handle it outside the markdown pipeline.

## The Complete Security Configuration

Here's how it all fits together in my unified processing pipeline:

```typescript
const processor = unified()
  .use(remarkParse)
  .use(remarkGfm) // GitHub Flavored Markdown
  .use(remarkFrontmatter)
  .use(remarkRehype, {
    allowDangerousHtml: false // Never allow raw HTML
  })
  .use(rehypeSanitize, {
    // The restrictive configuration above
  })
  .use(rehypeSlug) // Add IDs to headings
  .use(rehypeReact, {
    Fragment: jsxRuntime.Fragment,
    jsx: jsxRuntime.jsx,
    jsxs: jsxRuntime.jsxs,
    components: {
      pre: createPreComponent // Custom code block handling
    }
  })
```

I also handle code blocks specially, replacing HTML `pre` elements with my custom React component for better control:

```typescript
const createPreComponent = ({
  children,
  className
}: {
  children?: React.ReactNode
  className?: string
}): React.ReactElement => {
  return CodeBlock({ children, className })
}
```

This setup gives me confidence that my content processing is truly secure. The implementation lives in `src/lib/markdownRender.ts` in my [blog repository](https://github.com/rjleyva/rjleyva-writes).
