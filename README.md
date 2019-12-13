# JavaScript Advanced Functions: Collection-Processing Methods

## Learning Goals

* Pseudocode a real-world use of collection-processing methods
* Consult JavaScript's collection-processing methods' documentation

## Introduction

As programmers, we wonder about the world, come up with questions and then ask
a computer to help us manipulate data to find answers. Many of those questions
can be resolved by "polling" every member in a collection. We'd typically
"poll" each number in the collection and feed that value to a calculation (Look
up the French word For _x_) _or_ aggregate that value into a running value
(like a total).

Here are some real-world questions:

* "If these projected profits turned to losses, what would those losses be?"
* "What numbers in this data set are larger than 200? Larger than 2,000? Larger
  than an argument a user might provide?"
* "Which painting is the most valuable?"
* "Which painting is the least valuable?"
* "Do any of these children have a wet cough?"

These real-world questions involve:

1. Finding a collection of data, typically stored in an `Array` or `Object`
2. Visiting each element (`Array`) or pair (`Object`) in the collection
3. Doing some "work" with that element or pair
4. Returning a new collection **or** a new value based on the "work" that
   touched each element

When we say "work," we mean the evaluation of some expression that uses the
"current element." In JavaScript, you guessed it, that "work" is stored in
a function definition &mdash; be it a function declaration, a function
expression, or a function returned by invoking another function.

"Collection-Processing Method" is what we call a method provided by JavaScript
that:

1. "visits" each element or pair in a collection
2. tests those elements or pairs with "work"
3. returns a new collection **or** a value

Methods that behave in this way we'll say have the "Character of Collection
Processing."

In this module, we'll learn to use JavaScript's "Collection-Processing Methods"
to answer the type of question which involves "polling each member."

> **USAGE NOTE** In Ruby, all the methods that behave like this are called
> "Enumerable." There's no official collective term for methods that do this
> "polling each member" operation. In the rest of this module, we'll call them
> "Collection-Processing Methods." This isn't a hard-and-fast term that
> programmers use in daily practice, but all JavaScript programmers know that
> there's something similar to the methods we're about to introduce, so nobody
> would look at you too strangely for speaking of "JavaScript's Collection
> Methods."

## Pseudocode a Real-World Use of "Collection-Processing Methods"

Let's consider how a real-world need might drive us to think and behave in
accordance with the "Character of Collection Processing."

True story: someone close to us got married last year. In anticipation of his
destination wedding and fabulous honeymoon in Italy, he was determined to
reduce his chances of getting sick. The only problem, he takes public transit
every day to work.

His **Question** was: "How can I avoid being sick for these special occasions?"

Doing some research, he realized he could reduce airborne infection risk by
_wearing a surgical mask_. But he didn't want to wear one all the time so he
decided to implement the following modification to his behavior:

> **PSEUDOCODE**: Below we're going to use "pseudocode." It's something that
> looks a bit like code, but we're not expecting that it would run. It's just a
> convenient way to express a problem's solution in a way like code, but far
> less demanding. It's common to find programmers "sketching" a problem or a
> phenomenon in pseudocode because it's usually shorter to write than English,
> and, once you learn programming, it's a handy way to communicate with other
> programmers.

```js
while onTheTrain
  if iHearASickSound
    myMaskStatus = true
  end
end
```

The method name `iHearASickSound`'s pseudocode looks like
this:

```js
def iHearASickSound(passengerNoises)
  # Given a collection of passengers' sounds ["coughing", "yawning", "sneezing", "singing Jamaican traditional folksong"]
  # If any of them are sick sounds: cough, yawn
  # return `true`; else, return `false`
end
```

If we were to encode this, we might write the (real code, not pseudocode) the
method as:

```js
function iHearASickSound(passengersSounds) {
  for (let i = 0; i < passengersSounds.length; i++) {
    if (passengersSounds[i] === "coughing" ||
        passengersSounds[i] === "sneezing" ) {
      return true
    }
  }
  return false;
}

iHearASickSound(["coughing", "foo", "bar", "bin", "bat"]) //=> true
iHearASickSound(["sneezing", "foo", "bar", "bin", "bat"]) //=> true
iHearASickSound([            "foo", "bar", "bin", "bat"]) //=> false
```

This is but one tiny example. If you don't live in a big city with public
transport, maybe you "poll" all the cars at a four-way stop sign to see who
arrived first. Perhaps you're a bit lax on your laundry and you "sniff test"
all the clothes on the floor _until_ you find the one that's least-offensive.

We use Collection-Processing Methods all the time in real life! They're
everywhere in life, so they're very useful to have in code as well.

## Consult JavaScript's Collection-Processing Method Documentation

JavaScript provides us _lots_ of Collection-Processing Methods. You can find
them listed the [Array reference][arrayref] documentation at MDN.

This module _will not_ duplicate the documentation and teach each one to you.
Part of becoming comfortable with programming is becoming comfortable with
finding answers in the documentation. We'll demonstrate two of the most
important collection processing methods, but you should familiarize yourself
with others. Since they all follow the same _character_, once you learn one or
two, the rest will be easy.

### Enumeration Versus Collection-Processing Methods

You might think, "OK, I get it, Collection-Processing Methods follow this
'Character of Collection Processing' thing and that seems sensible enough.
What's so hard here?"

If you're thinking that, then GREAT! You're on the right track. The good news
here is that you understand "enumeration" as an abstract practice and that's
_exactly_ where we'd hope you'd be. You're doing great!

The trouble comes in when we talk about _coding_ with JavaScript's Collection
Processing methods. Specifically, the code can get confusing when we need to
_abstract_ out the "work" that we should apply to each element. To feel truly
comfortable with Enumerable methods, we have to understand the challenging
coding ideas of:

* Capturing work (but not _doing_ it) using (anonymous) functions
* Doing the work and passing it arguments based on visiting each element or
  pair in the collection. This is called invoking the method.  As a surprising
  monkey-wrench that causes tons of bugs, we'll need to reckon with JavaScript's
  "execution context" when we do the work (more on that later!)
* Gathering a new collection **or** combining the individual results into an
  aggregate result


If this sounds complex, don't worry: we've built a stair-step of lessons to
help you get comfortable with the terminology and code of collection
processing. If this all sounds obvious and easy, we hope you're going to be
philosophically engaged and inspired by how well JavaScript mirrors human daily
activity.

With JavaScript's Collection-Processing Methods on your side, you'll tear
through complex questions with ease &mdash; and surprisingly few keystrokes!
We'll start our exploration in the next lesson.

## Conclusion

A wide number of problems have a solution that involves following the
"character" of collection processing:

Process a collection by visiting each element and do "work" on it in order to
return a new collection **or** an aggregate value. Understanding collection
processing in the big picture is the first step to understanding
collection-processing methods, which we'll begin to study in the next lesson.

[arrayref]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
