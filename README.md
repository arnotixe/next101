## Next.js App Router Course - Starter

This is the starter template for the Next.js App Router Course. It contains the starting code for the dashboard application.

For more information, see the [course curriculum](https://nextjs.org/learn) on the Next.js Website.

## findings

lately we need to set env variable ENABLE_EXPERIMENTAL_COREPACK=1 on vercel

## Arno's notes

- image's dimensions (aspect ratio, really)
- fonts done the right way become part of the bundla
- loading.tsx shows while waiting for slow server rendered pages
- use component wrappers to group
- use () to group layouts and logically (CAVEAT not-found on same route level)
- install use-debounce and wrap whatever function is executed from input events

Where you place your Suspense boundaries will depend on a few things:

How you want the user to experience the page as it streams.
What content you want to prioritize.
If the components rely on data fetching.
