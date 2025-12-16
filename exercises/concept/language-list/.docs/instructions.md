# Instructions

In this exercise you need to implement some functions to manipulate a list of programming languages. Some of the functions you'll be asked to define may exist for `List`, which is good to know for future reference, but for this exercise try not to use them!

## 1. Define a function to return an empty language list

Define the `new` function that takes no arguments and returns an empty list.

```
languageList.new : [Text]
languageList.new = todo "return empty list"
```

## 2. Define a function to add a language to the list

Define the `add` function that takes 2 arguments (a list of languages and a string literal of a language). It should return the resulting list with the new language added to the front of the given list.

```
> languageList.new
  |> languageList.add "Clojure"
  |> languageList.add "Unison"
  ⧩
  ["Unison", "Clojure"]
```

## 3. Define a function to remove the left-most language from the list

Define the `drop1` function that takes 1 argument (a list of languages). It should return the list without the first item. Calling `drop1` on an empty list should return an empty list.

```
> languageList.new
  |> languageList.add "Clojure"
  |> languageList.add "Unison"
  |> languageList.drop1
  ⧩
  ["Clojure"]
```

## 4. Define a function to return how many elements are in the list

Define the `size` function that takes 1 argument (a list of languages). It should return the number of languages in the list.

```
> languageList.new
  |> languageList.add "Elm"
  |> languageList.add "Prolog"
  |> languageList.size
  ⧩
  2
```

## 5. Define a function to determine if the list includes a given language

Define the `contains` function which takes 1 argument (a list of languages). It should return a boolean value. It should return true if the desired language is one of the languages in the list.

```
> languageList.new
  |> languageList.add "Unison"
  |> languageList.add "Clojure"
  |> languageList.contains "Unison"
  ⧩
  true
```

## 6. Define a function to reverse a given list

Define the `reverse` which takes in a list and returns the list with the elements in reverse order.

```
list1 =
  languageList.new
    |> languageList.add "Clojure"
    |> languageList.add "Scala"
    |> languageList.add "Unison"
    |> languageList.add "Elm"

> list1
  ⧩
  ["Elm", "Unison", "Scala", "Clojure"]

> languageList.reverse list1
  ⧩
  ["Clojure", "Scala", "Unison", "Elm"]
```
