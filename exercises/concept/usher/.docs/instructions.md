# Instructions

The following function makes use of Unison abilities to keep track of a running count of parties entering a theatre. 🎭

The `usher` function itself is fairly simple, it takes in a list of tickets representing a party and lets parties in the door until the theater is full. If a number of tickets in in a party is greater than the remaining seats, a separate overflow list is started, otherwise the total count is incremented and the party is added to the theater.

However, the original author has left the ability handler writing up to you! Without a handler providing the concrete behavior of the required `Counter` ability, the function cannot actually be run or tested.

```
usher : [Ticket] -> Nat -> Theater -> {Counter} Theater
usher party maxSeating = cases
  Main room ->
    currentTotal = !getCount
    nextPartySize = List.size party
    if currentTotal + nextPartySize > maxSeating then
      Overflow party
    else
      incrementBy nextPartySize
      Main (room ++ party)
  Overflow room ->
    Overflow (room ++ party)
```

The `Counter` ability is given to you as:

```
structural ability Counter where
  getCount : () -> Nat
  incrementBy : Nat -> ()
```

`getCount` is a "thunk" or ["delayed computation"][delayed-computations] that returns the current count when called.

`incrementBy` takes a number to increment the count by and returns `Unit`.

## 1. Implement a simple counter handler

You'll need to implement an ability handler called `Counter.run` that takes in the value to start the count from and determines what should be done when the request operations, `getCount` and `incrementBy`, are called.

```
Counter.run : Nat -> '{Counter} a -> a
Counter.run initialValue functionUsingCounter = todo "implement run"
```

Once this handler is implemented, we can use it in simple programs like:

```
program : Theater
program =
  runUsher = 'let usher [Ticket, Ticket] 10 (Main [])
  Counter.run 0 runUsher
```

Or even use our handler as a result of processing a list of attendees:

```
programWithList : Theater
programWithList =
  attendees = [[Ticket, Ticket], [Ticket, Ticket, Ticket], [Ticket]]
  runUsher = 'let List.foldLeft (theater -> party -> usher party 10 theater) (Main []) attendees
  Counter.run 0 runUsher
```

A number of other examples of calling the `Counter.run` handler are included for testing!

## 2. Return the total count alongside the value produced by the function

Without changing the implementation of the `usher` function, we'd like to be able to get the total count as well as the result of the function using the `Counter` ability.

```
Counter.runWithTotal : Nat -> '{Counter} a  -> (Nat, a)
Counter.runWithTotal initialValue functionUsingCounter = todo "implement runWithTotal"
```

Applying this to our particular case, this handler should return a tuple of the running total with the ending state of the `Theater`

```
programWithTotal : (Nat, Theater)
programWithTotal =
  attendees = [[Ticket, Ticket], [Ticket, Ticket, Ticket], [Ticket]]
  runUsher = 'let List.foldLeft (theater -> party -> usher party 10 theater) (Main []) attendees
  Counter.runWithTotal 0 runUsher
```

[delayed-computations]: https://www.unison-lang.org/learn/fundamentals/values-and-functions/delayed-computations/
