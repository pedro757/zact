# Boring

Nothing to see here...
🤐

`npm install zact`

```ts
// action.ts
"use server";

import { z } from "zod";
import { zact } from "zact/server";
export const validatedAction = zact(z.object({ stuff: z.string().min(6) }))(
  async (input) => {
    return { message: `hello ${input.stuff}` };
  }
);
```

```ts
// component.tsx
"use client";

import { someServerAction } from "./action";
import { useZact } from "zact";

export const zactTestComponent = () => {
  const { mutate, data, isLoading } = useZact(someServerAction);

  return (
    <div className="flex flex-col text-xl gap-4 text-center">
      <button onClick={() => mutate({ stuff: "testtestaet" })}>
        Run server action
      </button>
      {isLoading && <div>Loading...</div>}
      {data?.message}
    </div>
  );
};
```
