# Instructions

In this exercise you need to implement some functions to manipulate a list of programming languages. Some of the functions may exist for `List`, but for this exercise try not to use them.

## 1. Define a function to return an empty language list

Define the `new` function that takes no arguments and returns an empty list.

```
languageList.new : [Text]
languageList.new = todo "return empty list"
```

## 2. Define a function to add a language to the list

Define the `add` function that takes 2 arguments (a list of languages and a string literal of a language). It should return the resulting list with the new language prepended to the given list.

```
> languageList.new
  |> languageList.add "Clojure"
  |> languageList.add "Unison"
  ⧩
  ["Unison", "Clojure"]
```

## 3. Define a function to remove a language from the list

Define the `remove` function that takes 1 argument (a list of languages). It should return the list without the first item. Calling `remove` on an empty list should return an empty list.

```
> languageList.new
  |> languageList.add "Clojure"
  |> languageList.add "Unison"
  |> languageList.remove
  ⧩
  ["Clojure"]
```

## 4. Define a function to return the first item in the list

Define the `first` function that takes 1 argument (a list of languages). It should return the first language in the list.

```
> languageList.new
  |> languageList.add "Elm"
  |> languageList.add "Prolog"
  |> languageList.first
  ⧩
  Some "Prolog"
```

## 5. Define a function to return how many languages are in the list

Define the `count` function that takes 1 argument (a list of languages). It should return the number of languages in the list.

```
> languageList.new
  |> languageList.add "Elm"
  |> languageList.add "Prolog"
  |> languageList.count
  ⧩
  2
```

## 6. Define a function to determine if the list includes Unison

Define the `containsUnison` function which takes 1 argument (a list of languages). It should return a boolean value. It should return true if _"Unison"_ is one of the languages in the list.

```elixir
> languageList.new
  |> languageList.add "Unison"
  |> languageList.includesUnison
  ⧩
  true
```

## 7. Define a function to create a string from the list


```
> languageList.new
  |> languageList.add "Clojure"
  |> languageList.add "Unison"
  |> languageList.join ", "
  ⧩
  "Unison, Clojure"
```
