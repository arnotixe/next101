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
- _IDEA_ use queryprams for search state etc and pass the (clientside) queryparam as a prop to a SERVER component (client list, invoice list etc)
  - this will auto rerender the servercomponent (with suspense magic) without server actions
- using form action to pass a server action - use JS BIND

```
  const updateInvoiceWithId = updateInvoice.bind(null, invoice.id);
  return <form action={updateInvoiceWithId}>{/* ... */}</form>;
```

- Using a hidden input field in your form also works (e.g. <input type="hidden" name="id" value={invoice.id} />) -- this could leak sensitive data though

- placement of Suspense boundaries will depend on a few things:
  How you want the user to experience the page as it streams.
  What content you want to prioritize.
  If the components rely on data fetching.

- Error boundary:
  - error.tsx in a folder (Must be a client component). see the example error.tsx for (error, reset)=> params
- const [state, formAction] = useActionState(createInvoice, initialState);

  - form action={formAction = taps into the server action and updates the state object (with e.g. state.errors)

- NextAuth use: proxy.ts and some config. proxy is a special file, not unlike middleware

## To study:

- data access layer (standardized, strip things and return known interfaces) https://nextjs.org/blog/security-nextjs-server-components-actions
  - in other words: only pass to frontend whateven the frontend should see (server side filter)

## Bugs:

chapter 12, the fetchInvoice throws, but should instead return null (or have try/catch in the component too)

    // throw new Error('Failed to fetch invoice.');
    return null;

}
}
Now that you know the invoice doesn't exist in your database, …
