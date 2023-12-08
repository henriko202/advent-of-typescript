# Prompt

## Organize Santa's List

[The elves walk into work early on the morning of December 5th. A sign that reads "we're all about passion, not just paychecks" hangs above the entrance to the factory floor.]

It's been a tough year for Santa's workshop. The elves are a little behind schedule on getting Santa his list. Santa reallly really likes to see the full list of names far in advance of Christmas Eve when he makes his deliveries.

Normally the elves get lists like this

```
const badList = ["Tommy", "Trash", "Queen Blattaria", /* ... many more ... */];
const goodList = ["Jon", "David", "Captain Spectacular", /* ... many more ... */];
```

And they copy-pasta all the values into a TypeScript type to provide to Santa like this

```
type SantasList = [
"Tommy", "Trash", "Queen Blattaria", /* ... many more ... */
"Jon", "David", "Captain Spectacular", /* ... many more ... */
];
```

But there's a problem.. There's one elf on the team, Frymagen, that constantly reminds the others how incredible his Vim skills are. So he has always done it in years past. However this year, Frymagen got one of those MacBook Pros without the escape key and his Vim speed is drastically reduced. We need to find a better way to get Santa his list.

Let's implement `SantasList` such that it can be passed the types for the `badList` and `goodList` and it will return a TypeScript tuple with the values of both lists combined.

# Explanation

The `SantasList` type is a generic type that represents a list of names. It has two type parameters: `T1` and `T2`, both of which must be arrays (or more specifically, readonly tuples) of any type (`unknown`)

The SantasList type uses the spread operator (`...`) to create a new tuple type (combined list) from two separate tuples (or lists), this type will include all the elements of T1 followed by all the elements of T2.
