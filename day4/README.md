# Prompt

## Christmas Present Delivery Addresses

[a conversation in the North Pole kitchenette on the morning of December 4th between Santa and the head elf, Bernard]

[Bernard] This is bullshit, Kris. I've been leading the Elves for 200+ years. Don't you trust that I know what I'm talking about?? WE NEED TO GROW THE TEAM. We're running a skeleton-crew here.

[Santa] Remember, we're like a family here; we all make sacrifices! We're still a startup!

[Bernard] I swear to you. I think if I hear another hussle-culture quip from you.... I think my little elf head will explode.

[Santa] If you can stick to it now and get us through one more year, there will definitely be rewards down the line.

[Bernard] I don't know why I even bothered asking...

Clearly, Bernard is a bit disgruntled. Can you blame him? Alas, there's still more work to do. Bernard walks away and mutters to himself:

[Bernard] Guess it's time to drag myself through another pointless TypeScript type challenge with no practical application.

Poor Bernard. Let's help him out.

Today's task is to craft a type (`PresentDeliveryList`) that takes an object type as an input and then replaces the values at each property with an `Address`. We don't know in advance what properties will be provided, which is why it needs to be a generic type. Otherwise Bernard would probably just copy/pasta it to get through the day.

# Explanation

The `PresentDeliveryList` type is a bit more complex. It's a generic type that represents an object where each property is of type `Address`. The keys of this object are determined by the type variable `T`.

In this type, `T` is a type variable, a stand-in for any type. The `[K in keyof T]` syntax is a mapped type. It's creating a new type by transforming the properties of `T`. In this case, it's taking each key of T (represented by K) and mapping it to the `Address` type.

In other words, a `PresentDeliveryList<T>` is an object that can have any keys, but each key must correspond to an `Address`.
