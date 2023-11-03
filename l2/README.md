# L2: Building a dashboard app using Next.js

<https://nextjs.org/learn/dashboard-app>

## Overview

### Goals
- Focus on learning Next's app router framework
- Building full stack apps using Next

### End product

A financial dashboard app with features:
- public home page
- login page
- some pages behind auth
- crud on invoices

### Stated goals of the tutorial

To learn:
- Styling
- Optimizations - images, links, fonts.
- Routing
- Data Fetching - setup db on vercel. best practices for data fetching
- Search & Pagination
- Mutating Date: using React Server Actions + cache re-validation.
- Error Handling
- a11y
- auth
- metadata: prepare app for social sharing

## Chapter 1: [Getting Started](https://nextjs.org/learn/dashboard-app/getting-started)

[Starter Repo](https://github.com/vercel/next-learn/tree/main/dashboard/starter-example)

```
npx create-next-app@latest nextjs-dashboard --use-npm --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example"
```

### Notes
- can use something like [prisma](https://prisma.io) to automatically generate types from db schema.

## Chapter 2: [CSS Styling](https://nextjs.org/learn/dashboard-app/css-styling)

- adding global css to app
    - import `global.css` to the root layout `/app/layout.tsx`

- tailwind vs css modules
- `clsx`

### Things I don't understand:

In `global.css` what does the following mean:

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- where do they come from?
- how is it wired up?
- is it specific to next.js?
- also vscode complains about it
    - seems like it is a [known](https://byby.dev/at-rule-tailwind) [problem](https://www.codeconcisely.com/posts/tailwind-css-unknown-at-rules/)
    - fixed by:
        - installing the tailwind css extension
        - setting a file association rule to tell vscode that css file are actually tailwind css files.

### Things learn more

- Tailwind CSS

## TODO
