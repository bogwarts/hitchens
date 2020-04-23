---
title: Big O Notation
category: literature
layout: post
---

# Big O Notation

### An intuitive understanding to describe the quickness of an algorithm. We do not mull over the formal definition as to not exhaust you. If you are in search of a challenge or a well chosen bedtime story -- see <a href="https://en.wikipedia.org/wiki/Big_O_notation" target="_blank">here</a>


## I need a metaphor
![alt text]({{site.baseurl}}/assets/images/demystifying_datastructures/0-introduction/alphabet.png "Alphabet Big O")


Say that we have a phone book with 26 names in it (one for each letter of the alphabet).

If we wanted to search for *Zoura Zubiri*, one strategy would be to go through the names one by one, until I reach Zoura. Lets say it takes me 1 second to read each name. So for the 26th name, it took me 26 seconds to reach Zoura.

<figure class="image">
  <img src="{{ site.baseurl }}/assets/images/demystifying_datastructures/0-introduction/phonebook_turning.gif" alt="phonebook big o">
  <figcaption>Figure 1. 1, 2, 3...26 seconds in total to finally find Zoura Zubiri</figcaption>
</figure>

Say that we have a phone book with 26 names in it (one for each letter of the alphabet).

If we wanted to search for *Zoura Zubiri*, one strategy would be to go through the names one by one, until I reach Zoura. Lets say it takes me 1 second to read each name. So for the 26th name, it took me 26 seconds to reach Zoura.

<figure class="image">
  <img src="{{ site.baseurl }}/images/demystifying_datastructures/0-introduction/phonebook.png" alt="phonebook big o">
</figure>

I know that Z is later than M, so I ignore the first half. This means there's half the amount of letters I have to search!

<figure class="image">
  <img src="{{ site.markdown_url }}/0-introduction/alphabet_cross_0.gif" alt="phonebook big o">
</figure>
<figure class="image">
  <img src="{{ site.markdown_url }}/0-introduction/phonebook_ripping.gif" alt="phonebook big o">
</figure>

It's a good strategy so we continue. We split right down the middle of the second half. That gets me to T.

<figure class="image">
  <img src="{{ site.markdown_url }}/0-introduction/alphabet_cross_1.gif" alt="phonebook big o">
</figure>

 I split again that gets me to W, and I split again, that gets me to W, then Y, and then I won't have to split again and hit Zoura. That takes about 5 steps, so 5 seconds.

<figure class="image">
  <img src="{{ site.markdown_url }}/0-introduction/alphabet_cross_full.gif" alt="phonebook big o">
</figure>


## So whats the deal with "big O" then?


Lets think about what just happened there. Our phone book has <b>26</b> names, and in our first strategy, I had to read <b>26</b> names. If our phone book had <b>1000</b> names, I would have to read <b>1000</b> names to find the last one.

But, in the more intelligent approach we just discussed, with 26 names, I only had to read through <b><i>5 names</i></b> to find Zoura! But heres the amazing thing: if we had twice as many names (52 names), would I have to read through **twice** as many names? Nope! I'd only have to read one more, since every step cuts the number of letters we are looking at in half.
<figure class="image">
  <img src="{{ site.markdown_url }}/0-introduction/alphabet_long.gif" alt="phonebook big o">
  <figcaption>Figure 8. The runtime does not scale with the input size n/figcaption>
</figure>

So in our first strategy, if we had <i>n</i> names in our phone book, we have to read through ```n``` names.

In our second strategy, if we had <i>n</i> names in our phone book, we only have to read through ```log(n)``` names.

## But wait!

Something doesn't feel right here. Why did we choose the name Zoura to search for. What if we searched for the name Adam (the first name in the phone book). In this case, our second strategy would still take 5 steps to find Adam. But the first strategy, would take only 1! So how could we say the second strategy is better? Turns out, <b>the only thing most of us care about is the worst case for each strategy</b>. Why?

## Computers are fast, but not that fast

In a phone book with 26 names, a computer using both strategies would find the name instantly. But, lets say you have a phone book with 2 billion names, (which is what Facebook is). In this case, if we tried to find the last person in the phone book with our first strategy, our computer would have to read through 2 billion names. But with our second strategy, we would only have to read through: log<sub>2</sub>(2 billion) ~ 31 names.

## What does this mean in code?

Let's take a look at this array of names
 ```python
 [ 'Alatar Atlantes', 'Blaise Babbits', 'Cersei Crimmins', 'Darman Dane', 'Erlin Erpero' ]
 ```
 A computer is dumb, and can only access elements one by one. A sequential search to Elon would take **5** steps. But a binary search would only take **3**. We'll split down the middle and see that it must be in the half that has ```['Darman Dane', 'Erlin Erpero']```. We split one more time until we reach ```Erlin```.

## Summary

 ```Big O``` notation tells you the number of steps it takes to accomplish a task relative to the number of elements in your input. ```Big O``` might refer to worst case, average case or best case.

Oftentimes, ```Big O``` is defined as the worst case scenario.

So in the example above, since you have 26 elements and it took 26 steps to accomplish your task, a sequential search costs, at worst, ```O(n)``` time, where n is the number of elements involved. However, the second strategy, a *binary search* costs ```O(log n)``` steps relative to n elements.

 Another way to figure out what the ```Big O``` is, is to ask yourself, at worst, how many operations do I need to do / elements to access to accomplish my goal?


## Additional notes: But it's not exactly log(n)!
You are right in that  log<sub>2</sub>(2 billion) is not exactly 31. But when it comes to defining the runtime complexity of a function, we only care about how it scales with the input.

```O(n)``` would be considered *equivalent* to ```O(2n)``` and *equivalent* to ```O(n + 2)```. Why? We care about how it behaves when ```n``` approaches to infinity. At that point the constant is negligible.

When you see 10000000000000000000000000000 gajillion galleons from Grinbbotts...does having 2 more than your mortal enemy matter?
