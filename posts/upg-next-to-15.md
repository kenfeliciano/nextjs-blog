---
title: Upgrading Next.js to version 15 (from 14)
date: '2025-06-10'
---

## Update Plan

My plan is to do what the dependabot email said and update next 14 to a later version of next 14. But, I was reading about Copilot for grins. I'm really not going to bond with AI I think, but what the heck. I know how to update next.js so let's see it work.

## Copilot

In Copilot check, I just said `update next.js`. I think that was it! I don't think I said `bump next.js to latest version of next.js 14` so instead of getting that, it updated me to the latest version.

```output
Copilot Output:
npm install next@latest
```

It ran it by itself and I tested both `dev` and `build` scripts. Everything worked fine.

## Brief Analysis

So, did it do a good job? It was obviously my fault for not specifying things and just clicking on buttons. But it works right?

If I search for [how to upgrade next.js](https://nextjs.org/docs/app/guides/upgrading/version-15), the documentation says the minimum versions of `react` and `react-dom` are both 19. It didn't update either of these.

I suppose it is up to me, the human to do that.

```bash
npm install react@latest react-dom@latest
```

## More testing

Does it work still? Does any of this matter with such a trivial example site? I wish it would have been smart enough to handle all those requirements. That's the thing that I still have a problem with regarding all these magical packages. When I run into blockages, it's often because I cannot seem to apply updates properly.

Both `dev` and `build` are still working locally. I'll assume all will work when I push these changes.

## Conclusion

Close Copilot. If you would have updated react and react-dom as well as next I would have been impressed.

Close Ken. If you would have just said to not do a major update...somehow.
