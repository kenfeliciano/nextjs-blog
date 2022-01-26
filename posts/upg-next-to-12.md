---
title: 'Upgrading next.js to version 12 (from 11)'
date: '2022-01-25'
---

## Thanks Dependabot!

Dependabot told me that nanoid is too old. It was version 3.1.25 and it needs to be >= 3.1.31. The fix is of course to just update the `dependencies` section (or `devDependencies`) to a newer version for this package that I've obviously added to my project. You've seen these right?

### Remediation

Upgrade **nanoid** to version **3.1.31** or later. For example:

```json
"dependencies": {
  "nanoid": ">=3.1.31"
}
```

or…

```json
"devDependencies": {
  "nanoid": ">=3.1.31"
}
```

### But...

I don't have this package in my package.json! Where is it? I've recently bumped into `npm ls` which is quite helpful for figuring this type of thing out.

```bash
npm ls nanoid

learn-starter@0.1.0 {thepath}\nextjs-blog
`-- next@11.1.0
  `-- postcss@8.2.15
    `-- nanoid@3.1.25
```

So, I've got to upgrade next.js to 11. I figured, this is the easiest website in the world. I mean, it doesn't even have nice formatting for code blocks (as I can now see). I checked out the [Next.js Upgrade Guide](https://nextjs.org/docs/upgrading) and it looked so easy, I thought I'd try it!

## Steps to upgrade

I'm using `npm` so for `yarn` see their document. See it anyway really!

```bash
npm install react@latest react-dom@latest
npm install next@latest # They said to install next@12 but I wanted the latest at this point
```

Now what's up with nanoid?

```bash
npm ls nanoid

learn-starter@0.1.0 {thepath}nextjs-blog
`-- next@12.0.8
  `-- postcss@8.2.15
    `-- nanoid@3.2.0
```

Everything worked perfectly out of the gate. 3.2.0 is **_way_** higher than 3.1.31 so I suppose I'm less vulnerable. Once again, this site keeps me on my toes, well, Dependabot does.
