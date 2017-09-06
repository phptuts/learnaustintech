---
layout: post
title: Android Lesson 1 Cliff Notes
excerpt: "Java Basics."
modified: 2017-09-05
categories: articles
comments: true
share: true
---
## Setup

Go here an install android studio.
https://developer.android.com/studio/index.html

## Java Basics

Two things
- Comments are ways to leave notes to yourself.  They look like this // 
- All programming statement end in a semi colon, ';'.  Look at it like the period of a sentence.

## Variables

There are 4 types of variables you need to know in order to build an android app.  
- String: Stores text data
- Boolean: Stores either true or false
- Integer: Stores whole numbers like 3, 5
- Double: Stores numbers with decimals like 3.44,323.2

Here is how it looks in action:

```
int age = 30;
double cupsOfFlours = 3.5;
String name = "Amy";
boolean iLikeIcecream = true;
boolean iLikeTraffic = false;
```

Variables have 3 parts:
- name
- value
- type

```
int age = 30;
age = age + 10;
Log.i("age", age);
```

So in our example "age" is the name of the variable.  30 is the value of the variable and int is the type of variable.  int = integer.


### Action Step: 

Create an App that display a toast message for each type of variable.  Put this code inside onCreate method.  This code is used when a the android app first starts up

```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    boolean isCarBlue = true;
    Toast.makeText(getApplicationContext(), isCarBlue, Toast.LENGTH_LONG).show();
}
```

## Methods / Functions

A method / function is a block of code that you can re use.  It can take input aka parameters and return output.  Methods must declare the parameters they take in a type of parameter that they return.  But it does not have too take in a parameter or return anything.

```
int addTwoNumbers(int a, int b) {
    return a + b;
}

int sum = addTwoNumbers(4,88);
```

Copy the code and put in the app you created.  Then Toast Message out the sum, but before you do tell the instructor what you think the sum is.

Note on variables.  Variables created out of the method can be used to outside and inside the method.  Instructor will demo with a simple app that changes state every time the button is tapped.

### Action Step:
Create an android app with a button.  Every time the button is clicked create a toast message that says you "You Rock!!!".  Your instructor will walk you through creating an example app that does something similar.  You will then try to build the app with knowledge you gained.


## Decisions

In order for your app do cool things you have to be able to tell it how to make decisions.  For example if a users gets 10000 points give the user a free life.  If I am driving send a text letting person sending me a text know that I am driving and won't be able to answer.

#### How if / else statements look

```
int age = 13;
int ageRequiredToWatchScaryMovie = 17;
if (age >= ageRequiredToWatchScaryMovie) {
    // Allow users to watch movie
}
else {
    // Tell user no
}
```

### Action Step

Create an app with a text a box and a button.  When user hits the button and your favorite color is inside the text box display in a toast message you guessed my favorite color.  If user fails to guess your favorite color TextView "Try Again".  Your instructor will walk you through creating everything but the if / else statement.


## WOW we have done a lot of work!!!


### Action Steps:

Create an app called tapper that will give a point to the user every time the user taps the button.  The points can be displayed in a TextView.  

Create a currency converter app from dollars to pounds.  This will have a EditText and a button.  You will display the results in a toast message.

Create an simple addition calculator app that takes in 2 inputs and add the results.  The sum will be displayed in a toast. 

Create your 2 favorite pictures.  Put every time the button is clicked the picture changes.  Hints:
- Google ImageView
- Google how to change an image view

Create your own simple apps.  Keywords are simple and funny.  Challenge signup for github and post the code to one your simple and funny apps.  Congrats your now building your portfolio. :)
  
Post questions in the comments below or shoot me an facebook message / email.

