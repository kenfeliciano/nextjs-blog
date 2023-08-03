---
title: Upgrading Next.js to version 13 (from 12)
date: '2023-08-03'
---

# Upgrading from Next 12 to 13

`Ref`: https://nextjs.org/docs/pages/building-your-application/upgrading/version-13

Let's see how easy this is!

## Install New Version

```bash
npm i next@latest react@latest react-dom@latest eslint-config-next@latest
```

This does not work! It's currently running react 17.0.2 and doing the install like this doesn't work. As soon as next tries to install the latest, it sees old react and fails. Error recommends adding `--legacy-peer-deps` which I've done before. I suppose that's the best solution when you **_know_** what you are doing. In this case, I know next and react are conflicting but if they are both upgraded, they won't conflict. Yes?

Also, updated `remark` and `remark-html` to latest.

### Version Compare

| Package            | v12     | latest   |
| ------------------ | ------- | -------- |
| next               | ^12.1.0 | ^13.4.12 |
| react              | ^17.0.2 | ^18.2.0  |
| react-dom          | ^17.0.2 | ^18.2.0  |
| remark             | ^13.0.0 | ^14.0.3  |
| remark-html        | ^13.0.2 | ^15.0.2  |
| eslint-config-next | NA      | ^13.4.12 |

## Does it **just** Work?

No! But that's okay, I wasn't done reading.

### Error 1: Invalid `Link` Component with `a` Component

Pre version 13, you had to nest an anchor tag, `<a>`, when you used the Link component, `<Link>`. That is no longer required or supported. There is a codemod for this

```bash
npx @next/codemod@latest new-link .
```

This worked great except it did not respect my `Prettier` settings. I just went to each file and saved it as there were only three files touched. And only two actually had the Link in it. Strange that.

After this, the site is back up and running. That was **_easy_**!

### Error 2: TypeError Related to `remark` When Clicking on Posts

I click on any existing post and get: `TypeError: (0 , remark__WEBPACK_IMPORTED_MODULE_3__.default) is not a function`
The key bit here is `default`. As the new version of remark does not export a default, the import has to change to use a named import.

```js
import { remark } from 'remark'
```

## Updates

### Image Component

The original tutorial (Next.js 11?) used a standard `<img>` element. The newer tutorials use the `<Image>` component. That was an easy replacement. As I was not using it previously, there was no reason to look at the codemod regarding that.

### App Directory

[Migrating from pages to app](https://nextjs.org/docs/pages/building-your-application/upgrading/app-router-migration#migrating-from-pages-to-app)
This does look interesting and it is a place where things I understand (or think I do) are being replaced.

> - Data fetching functions like `getServerSideProps` and `getStaticProps` have been replaced with [a new API](https://nextjs.org/docs/app/building-your-application/data-fetching) inside `app`. `getStaticPaths` has been replaced with [`generateStaticParams`](https://nextjs.org/docs/app/api-reference/functions/generate-static-params).

- `_document` file which I have not used yet. But that and `_app` should migrate to `app/layout.tsx`. Luckily, they can all coexist as long as there are pages.
- `<Head>` component is migrating to use built-in SEO support
