# Gardening Affiliate Blog

This is an SEO-optimized, responsive, dark/light mode supported affiliate blog built with AstroJS and Tailwind CSS.

## Tasks for GitHub Copilot

### ✅ Task 1: Initialize Astro project

```bash
npm create astro@latest
# Project name: gardening-affiliate-blog
# Template: Minimal
# Use Typescript: Yes
# Use Tailwind CSS: Yes
```

### ✅ Task 2: Set up file structure

Create the following structure:

```
/src
  /components
    Header.astro
    Footer.astro
    BlogCard.astro
    ToggleTheme.astro
  /layouts
    BaseLayout.astro
  /pages
    index.astro
    blog/
      [slug].astro
    about.astro
  /data
    posts.js
/public
  /images
```

### ✅ Task 3: Configure Tailwind for Dark Mode

`tailwind.config.cjs`:

```js
module.exports = {
  darkMode: 'class',
  content: ['./src/**/*.{astro,html,js,jsx,ts,tsx}'],
  theme: { extend: {} },
  plugins: [],
};
```

### ✅ Task 4: Create ToggleTheme component

```astro
---
const toggle = \`
  const html = document.documentElement;
  html.classList.toggle('dark');
  localStorage.theme = html.classList.contains('dark') ? 'dark' : 'light';
\`;
---

<button onclick={toggle} class="p-2">
  🌓 Toggle Theme
</button>
```

### ✅ Task 5: Blog post data

`src/data/posts.js`:

```js
export const posts = [
  {
    slug: "how-to-grow-tomatoes",
    title: "How to Grow Tomatoes Easily",
    excerpt: "Learn how to grow juicy tomatoes in your backyard...",
    date: "2025-06-29",
    image: "/images/tomatoes.jpg",
    tags: ["vegetables", "gardening tips"]
  }
];
```

### ✅ Task 6: Dynamic blog page

`src/pages/blog/[slug].astro`:

```astro
---
import { posts } from '../../data/posts';
const { slug } = Astro.params;
const post = posts.find((p) => p.slug === slug);
---

<Layout title={post.title}>
  <article class="prose dark:prose-invert">
    <h1>{post.title}</h1>
    <p>{post.date}</p>
    <img src={post.image} alt={post.title} />
    <p>{post.excerpt}</p>
  </article>
</Layout>
```

### ✅ Task 7: Layout with SEO

`src/layouts/BaseLayout.astro`:

```astro
---
const { title = "Gardening Blog", description = "Learn gardening and earn with affiliate links" } = Astro.props;
---
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>{title}</title>
    <meta name="description" content={description} />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="canonical" href={\`https://yoursite.com\${Astro.url.pathname}\`} />
  </head>
  <body class="bg-white dark:bg-gray-900 text-black dark:text-white">
    <slot />
  </body>
</html>
```

### ✅ Task 8: Add affiliate links

```astro
<a href="https://affiliate-link.com/greenhouse" rel="nofollow sponsored" class="text-green-600 underline">
  🌱 Buy this greenhouse on Amazon
</a>
```

### ✅ Task 9: Deploy

```bash
npm run build
npm run preview
vercel
```

