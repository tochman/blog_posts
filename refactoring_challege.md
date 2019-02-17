## Refactoring Challenge

I stumbled upon a really good blog post about working with models in Rails in a Behaviour-driven Development approach. It is written in 2016, so it is a bit old. The outlined approach and implementation are not bad in any way, on the contrary. [Ilija Eftimov](http://eftimov.net/), the author of the post, presents a flow that is quite similar to my own, and highligts some interesting points and examples that can bring clarity to how associations between models can be used and tested. Also, he make an argument and examplifies how business logic can be encapsulated to separate concerns and responsibilities. So far so good. Really good. 

While reading the post and running some tests and code in my console, I spotted some aspects of the presented solutions and tools used that could be improved upon. It struck me, that this could make out a good challenge for our students/alumni. Why not raise a few questions, do a mob session around the topic and see if we all can learn something?

Does that sound interesting? Let's get after it!

## The challenge
First, read the post. Its titled **How to Test Rails Models with RSpec** and can be found at https://semaphoreci.com/community/tutorials/how-to-test-rails-models-with-rspec. 

Scaffold a Rails application (or use the [Craft Academy Boilerplate](https://github.com/CraftAcademy/boilerplate)) 

Implement the outlined tests and models from the blogpost. That will take a while and put your rails skills to the test. As I mentined above, the post is a few years old, and a lot of things has changed since then (mostly small things, but small things matter). Make a list of things you spot needs to be chaged while implementing the solution.

Here comes the trick and your refactoring challenge:

1. The Author is NOT using factories. I would like you to refactor the tests to use Factory Bot.

2. While the author makes use of the Shoulda gem, the notation used in the tests is `should`. I would like you to refactor that to the more "modern" `is_expected` notation. 

3. In the post, the `BiddingEngine` logic is extracted to a Ruby class. I would argue that we could use a module instead. Why? 

4. Answer the Authors last question: _"What is your preferred way to test models? Do you use BDD in your everyday work? When testing, do you use the red-green-refactor cycle?"_

5. Finally, what did you learn while working on this challenge? Was it worth your time and effort? Is this kind of challenges relevant to your learning? 

## The flow

Work alone or with a pairing partner. Pairing up for this challenge will help a lot as you can discuss the solutions and research various topics together. **There are no right and wrong solutions in this challenge**. You either do it or you don't. ;-)

We will set up a mob session and discuss the solutions. If you can't take part, please submit your code as a GitHub link (with your thougts outlined in the README)