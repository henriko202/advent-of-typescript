# Prompt

## Is Santa Dyslexic?

[it's early Saturday morning and the team has been working overtime. Santa storms into the factory floor shouting..]

[Santa] Don't you elves take any pride in your work?!?! Others would love to have your job for much less pay! I asked for a simple type that will reverse strings!! How hard is that?!? What do we even pay you for??

[unfortunately, Santa is conveniently forgetting that the `Reverse` type was cut from the sprint (which... of course... he agreed to)]

[floor manager] Ok. We never got acceptance criteria for that ticket.

[Santa] How difficult is it to understand what Reverse does!? `'rehsaD'` should be transformed into `'Dasher'`, `'recnaD'` should be transformed into `'Dancer'`, `'recnarP'` should be transformed into `'Prancer'`.. DO I NEED TO KEEP GOING?

[floor manager] Well you might be surprised. For example, what should happen to multi-codepoint unicode characters?

[Santa] What are you on about with all that accessibility stuff again!

[floor manager] Accessibility is important, sir.

[Santa] Look, this is just an MVP. We can add accessibility later. Just get me my `Reverse` type! I'm having a hard time reading this stuff otherwise!

# Explanation

Now this is a fun one, we're using a recursive generic type.

```ts
type Reverse<Str extends string, Res extends string = ""> = Str extends `${infer FirstChar}${infer Rest}`
  ? Reverse<Rest, `${FirstChar}${Res}`>
  : Res
```

- `` Str extends `${infer FirstChar}${infer Rest}` ``: This is a string template literal type. It splits the string into two parts, the first character and the rest of the string. This is used as a conditional type, so if the string can be split, the type is true, otherwise it's false.
- `` Reverse<Rest, `${FirstChar}${Res}`> ``: This is the recursive part. We're calling `Reverse` again with the rest of the string and the first character prepended to the result.
- `: Res`: This is the base case. When the string is empty and can't be split, we return the result.

In other words, if `Str` can be split (`` extends `${infer FirstChar}${infer Rest}` ``), the `Reverse` type is called recursively with `Rest` as the new `Str` and `` `${FirstChar}${Res}` `` as the new `Res`. If Str can't be split, `Res` is returned.
