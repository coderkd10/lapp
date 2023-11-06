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
    - css modules great when:
        - prefer writing traditional css
        - keeping styles separte from jsx

- [`clsx`](https://github.com/lukeed/clsx)
    - easily toggle class names

- other styling options
    - sass: can import `.css` and `.scss` files
    - css-in-js libs: styled-jsx / styled-components / emotion

- [next.js styling docs](https://nextjs.org/docs/app/building-your-application/styling)


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
    - [utility classes](https://tailwindcss.com/docs/utility-first)

## Chapter 3: [Optimizing Fonts and Images](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images)

### `next/font`

Add custom fonts with `next/font`.

- **why?** To avoid ["Cumulative Layout Shift"](https://web.dev/articles/cls)
- [read more](https://nextjs.org/docs/app/building-your-application/optimizing/fonts)
- [reference](https://nextjs.org/docs/app/api-reference/components/font)

### `next/image`

Add images with `next/image`.

- **why?** If we manually add images using the `<img>` tag, then we need to take care of following manually:
    - ensure images are responsive on different screen sizes: desktop, mobile, etc.
    - manage image sizes for different devices
    - prevent layout shift as images load
    - lazy load images outside of viewport

- **what?** `next/image` provides `<Image>` component, which is extension of `<img>` tag. It takes care of optimizations such as:
    - prevent layout shift when images are loading.
    - resize images to avoid shipping large images to devices with smaller viewport.
    - lazy load images by default.
    - serve images in modern formats (e.g webp, avif, etc) where supported by browser.
- [read more](https://nextjs.org/docs/app/building-your-application/optimizing/images)

### more reading

- [MDN: improving perf with images](https://developer.mozilla.org/en-US/docs/Learn/Performance/Multimedia)
- [MDN: web fonts](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Web_fonts)

## Chapter 4: [Creating Layouts and Pages](https://nextjs.org/learn/dashboard-app/creating-layouts-and-pages)

### Goals

- so far the app just has the home page (`/`)
- will create more routes with layouts and pages
    - `/login` and `/dashboard` pages (using "file-sytem" routing)
- will create shared layout for multiple dashboard pages
- understand:
    - "colocation"
    - "partial rendering"
    - "root layout"

### Concepts

- `app/your/route/page.tsx`: exports a react component containing the UI for path `/your/route`

- "Colocation"
    - inside the `app/your/route` directory can also put our own files (ui components, test files, other related code) for that route. Only the contents of `page.[js|ts]` file will be publically accessible.
    - [read](https://nextjs.org/docs/app/building-your-application/routing#colocation) [more](https://nextjs.org/docs/app/building-your-application/routing/colocation)

- `app/your/route/layout.tsx`: UI that is shared between multiple pages


## Chapter 5: [Navigating Between Pages](https://nextjs.org/learn/dashboard-app/navigating-between-pages)

### Goals

- use the `next/link` component
- show active link using `usePathname()` hook
- client side navigation in Next.js

### Client side navigation

- what? using `<Link>` instead of `<a>`
- why? to avoid full page refresh

- learn more about [how navigation works](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#how-routing-and-navigation-works)


### Notes

- `use client`: declare ["Client Component"](https://nextjs.org/docs/app/building-your-application/rendering/client-components)
- next does automatic code spliting and prefetching

## Chapter 6: [Setting up DB](https://nextjs.org/learn/dashboard-app/setting-up-your-database)


