# RSPEC RESOURCES


#### This is a non-exhaustive list of resources related to Rspec.

[http://blog.teamtreehouse.com/an-introduction-to-rspec](http://blog.teamtreehouse.com/an-introduction-to-rspec)

[http://www.anchor.com.au/wp-content/uploads/rspec_cheatsheet_attributed.pdEC
](http://www.anchor.com.au/wp-content/uploads/rspec_cheatsheet_attributed.pdEC)

Here's the RSpec cheatsheet:

[http://www.anchor.com.au/wp-content/uploads/rspec_cheatsheet_attributed.pdf](http://www.anchor.com.au/wp-content/uploads/rspec_cheatsheet_attributed.pdf)

<br/>

##RSPEC TESTING (Summary)

1. Determine what functionality you want
2. Write a test that expects it to work
3. Provide code that passes the test

<br />

##RSPEC Quiz Question

####Q1 // : Below we have a file called animals.rb. Don't worry about the code in there, just explain in bullet points (or as a numbered list) the steps needed to SETUP and RUN tests on this file using rspec. Your answer should be a list (and might start with $ mkdir spec and finish with $ rspec .... )	

```
class Vertebrate 
def spine
true
end
def describe
"I have a spine"
end
end

class Aves < Vertebrate
def initialize
@eggs = true
@fly = "can fly"
end 

def eggs
@eggs
end
 
def describe
"I #{@fly}"
end
end
```

###Answer:

*1/ in the same directory as animals.rb $ mkdir spec <br/>
2/ $ cd spec <br/>
3/ $ touch animals_spec.rb <br/>
4/ $ cd .. <br/>
5/ $ rspec --init* <br/>



<br/>
<br/>

#Grant's MARKDOWN:

#Ruby Rspec
---

Let's dig into some really groovy testing with Rspec!

##Rspec & Ruby

###Learning Objectives
* Understand & articulate the value of testing in programming
* Be able to setup Rspec in a project
* Be able to write tests to cover:
    - Instance Methods
    - Class Methods
* Run your test suite

##What is Rspec & why do we care?

Rspec is a testing framework. It allows us to write code that tests other code. With Rspec, we write a bunch of spec (short for _specification_) files for the different Ruby/Rails files in our project.

Then, before we push our code to a production server or share it with one of our teammates, we can run the suite of rspec tests to make sure our code behaves as expected.

*But why do we care?* Because testing takes a lot of stress out of programming. We can write tests to state the way our code should work, then we can 

* Test our code everyday.
* Know that the code we wrote today doesn't break something else we wrote months ago.
* Ensure we only push quality code to production.
* Prevent bugs that would ruin our users' experiences (or worse... Imagine if you're a bank!)
* Share tests with your team so even if they didn't write your code, they can test it to make sure it works.

##Let's Write A Spec!
---

###Making A Calculator

Make a new directory called `ruby-rspec`. Inside that folder, create another folder called `lib`.

Create a new ruby file called `calculator.rb`. Then write the Ruby code below to setup a basic calculator class:

```
class Calculator

end
```

Now, let's add a really simply multiplication Class function that always returns '1'.

```
def multiply
  return 1
end
```

###Mini-Ruby Lab

Great! Now, it's your turn. In pairs, I want you to take a few minutes to write the ruby logic for the multiply method. It should:

* Take an array as it's argument
* Multiple the numbers in the array together
* Return the Integer product of the numbers

####10 Minutes Later...

Here is my solution. Your may be different but if it works, we're good!

```
class Calculator

  def self.multiply(numbers)
    product = 1
    
    numbers.each do |num|
      product *= num
    end

    return product
  end

end

```

###Introducing Rspec

Let's add rspec to our project. First we need to install Rspec, which is a Ruby gem. From the Command Line, run this command: `$ gem install rspec`

Once that is installed, we can add rspec to our little project using `rspec --init`. Run that command now, from the Command Line, at the root of our project (not inside `lib`!).

```
$ cd ..
$ rspec --init
```

Rspec will tell you what it created. Let's talk about them.

* `.rspec` is a hidden file that loads Rspec and has some basic options. Whenever we run Rspec this file is run.
* `/spec` is the default spec folder where we keep all of our spec files. This is a convention for Ruby and Rails projects.
* `/spec/spec_helper.rb` is a configuration file for Rspec. We can adjust default settings, add additional testing tools, and adjust how Rspec behaves from there.

For now, we're only going to adjust one thing. In your `.rspec` file, add this line at the bottom: `--format documentation`. This changes how Rspec shows our test results. We can also do `progress`, which is a format that uses dots instead of printing each test.

###Writing A Spec

Create a file inside `/spec` called `calculator_spec.rb` (notice spec files are Ruby files... rspec is written in Ruby).

At the top of the file, we require the Ruby file we want to test. Then below we write a `describe` block.

```
require 'calculator' # rspec assumes this is a Ruby file and it looks by default in our project's `/lib` folder so we don't need to be more specific than 'calculator'

describe Calculator do

end
```

Let's write a test!

```
require 'calculator'

describe Calculator do

  # group tests inside describe blocks, one for each method. All of those are grouped inside the describe block with the class (Calculator above).
  describe ".multiply" do
    
    # Our first spec!
    it "multiplies an array of numbers together" do
      expect( Calculator.multiply([2,5,6]) ).to eq(60)
    end
  end

end
```

We group specs by the method they test. You can see above I added a `describe ".multiply" do/end` block in our test. Then we write out specs for that method inside that block.

_Convetion:_ describe blocks for a class method start with a period (`".multiply"`) and describe blocks with an instance method start with a hashtag (`#spine`).

Look at the spec inside of the `".multiply"` describe block.

The first line of the spec is it's name. That will get printed when we run rspec with the documentation format or if the test fails. The name does not mean anything or have any bearing on how the code is tests. It's just a name.

The second line `expect( Calculator.multiply([2,5,6]) ).to eq(60)` is the entire test. 

In rspec, we write everyhing as an expecation. Basically, this line says

1. When `Calculator.multiply( ... )` runs...
2. with the argument `[2,5,6]`, ...
3. we expect the result to equal the integer 60. 
4. If it doesn't, the test failed... 
5. and our code doesn't work as expected.

Let's run it! We can run all the tests in our project by going to the root of our project and using the `rspec` command:

```
$ cd .. # if you're in /lib or /spec
$ rspec
```

Green means good, Red means bad.

Now, let's add a few more tests:

```
require 'calculator'

describe Calculator do

  # ... our first test is here

  it "accepts string numbers" do
    expect( Calculator.multiply(['2', '8', '1']) ).to eq(16)
  end

  it "accepts mixed input" do
    expect( Calculator.multiply(['3', 3, 4]) ).to eq(36)
  end

  it "returns nil when it receives an empty array" do
    expect( Calculator.multiply([])).to be_nil
  end

end
```

Now that we have four tests to cover our Multiply function, run them.

Did they fail? That is expected! 

This is a common pattern in programming, it's called *Red-Green-Refactor*.

###Red-Green-Refactor

Here is the philosophy

* *Red*: Write tests before you write the actual code. These are like fences around your code that describe exactly how you want the code you're writing to work.
* *Green*: Write the code. It doesn't need to be perfect or pretty. Just write whatever code is the easiest or most obvious way. Continually run your test suite until all your tests pass.
* *Refactor*: Once you've written code that successfully passes your tests (which are complete and rigorous, right?), you can refactor the code. Fix the ugly bits, make your code faster or easier to read. Use your tests as guides so you know your optimizing isn't breaking anything.

###Lab

Take time now to get your test suite passing, then take some time to refactor your Multiply method once it works. Do this in pairs now.

####My Solution

```
class Calculator

  def self.multiply(numbers)
    return nil if numbers.empty?
    
    total = 1
    
    numbers.each do |num|
      total *= num.to_i
    end

    return total
  end

end
```

##Spec For Animals
---

Let's write a spec for the Animals Ruby classes we wrote yesterday. Copy [animals.rb](animals.rb) into a new folder called `/animals` and then we can setup Rspec like above. Now, let's write a Spec for `Vertebrate` and one for `Aves`.

_note: Notice the animals don't use puts anymore but simply return strings. That is slightly different from yesterday's class. Better to have methods return a String. Otherwise have to test against Standard Output which is both advanced and almost never done in the real world._

##Wrap Up
---

* Why Test?
  - Testing bring rigour and stability to programming.
  - Testing makes it easier to work on a team.
  - Testing makes it easier to ship good code and prevent regression (backsliding)

##Questions?
---

