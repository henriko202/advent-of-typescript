# Prompt

## Filtering The Children (part 2)

[transcript of a slack conversation at 11:23pm between Santa and Chipper (one of the elves that worked on the filtering code from yesterday)]

[Santa] We've got a big problem. That code that you gave me yesterday doesn't work!

[Chipper] what doesn't work about it?

[Santa] It turns out I need the data formatted in a completely different way! The inputs and outputs all need to be different.

[Chipper] ok, so it sounds like the requirements have changed. did you ask my manager? it's late and I'm relaxing. I'm in the middle of a game of League of Legends.

[Santa] Is that like RuneScape? Well anyway, would you mind helping me out in a pinch? Think of this as paying your dues for a better position later!

[Chipper] ok. I guess.

[Santa] Wonderful! Here are the inputs and outputs! That oughta be plenty for you! Ok, I gotta get some rest for a golf game I'm having tomorrow. Signing off!

Developing From The Tests
As you can see, sometimes leadership like Santa manage to convince themselves they have fantastic product vision, you'll get little more than basic inputs and outputs, and you'll have to figure out the behavior from there. Don't be flustered. Take a look at the tests and try to figure out what the behavior is supposed to be.

Start by identifying the inputs for our `AppendGood` type. Ask yourself if there should be any generic type constraints on the inputs (there may not need to be, or at least right away).

Then try to set up a scaffold that will at least return the same values for each property. Your next step is to transform the properties somehow..

# Explanation

Now this is a bit more complicated, the `AppendGood<T>` type represents a new type where each key is a string that starts with "good\_" followed by the original key name. This is achieved using the `as` keyword and template literal types (`good_${string & K}`).

Talking a bit more in depth about the `AppendGood` type:

- `K in keyof T`: This is a mapped type. It's creating a new type by transforming the keys of T. K represents each key of T.
- `` as `good_${string & K}` ``: This is a template literal type. It's creating a new string by appending "good\_" to the original key name. The string & K part is a type intersection that ensures K is treated as a string. This is necessary because K is a generic type parameter and could be any type.
- `T[K]`: This represents the type of the value at key `K` in `T`.
