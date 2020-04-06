

# Introduction to self driving car

## 2. Bayesian Thinking

### 2.1. Introduction

**The wonderland of Baye's law** 

Normal AI people : 

* Assume that everyone knows everything about the world
* When the world is wrong, it would do fatal mistakes

Baye's rule: 

* Permits the possibility that world might be uncertain, we might not know and we might have to explore the world to gain information
* Mathematical framework to gather information is called Statistics
* Baye's rule is at the core of statistics



**Pre-requisite:**

linear algebra  					: https://www.khanacademy.org/math/linear-algebra 

Probability and statistics	: https://www.khanacademy.org/math/statistics-probability 

Intro to algebra  					: https://www.udacity.com/course/intro-algebra-review--ma004 

Algebra 1								: https://www.khanacademy.org/math/algebra 

Algebra 2								: https://www.khanacademy.org/math/algebra2 

Basic geometry					: https://www.khanacademy.org/math/basic-geo 

Trigonometry						: https://www.khanacademy.org/math/trigonometry 



**Course overview**

1. Joy ride
2. Probability
3. Conditional probability
4. Programming probability in python
5. Baye's rule
6. Programming Baye's rule and world representations
7. Robot localization
8. Histogram filter in python 



### **2.2. Project: Joy Ride**

**Project overview**

* Write code to control simulated car

* 3 parts

  * **Part 1: Drag Race**
    *  In this part you'll write code that lets a car jump over a grove of trees. This might not be a *common* scenario for a self driving car but it will get you familiar with the programming interface.
  * **Part 2- Circular Track**: 
    * You'll write code that lets a car navigate a circular track. In doing so you'll explore the relationship between *steering angle* and *turning radius*.
  * **Part Three - Parallel Park**: 
    * In this part you'll write a sequence of instructions that successfully parallel parks a car.

* #### Tip

  For Part Three, the simulator contains a little bit of noise each time you launch it. To help account for this, consider spending a second or two of `time` traveling slowly forward in the simulator before reversing into your parallel parking. You should also consider using a fairly low vehicle velocity at all times.

* **Project rubric:**

  * https://review.udacity.com/#!/rubrics/1206/view
    * Successful Completion of Maneuvers
      * Part 3 - park function works correctly
        * The `park` function causes the car to parallel park in the right lane without going off the road or hitting any of the other vehicles.

* Cheat sheet

  ![nd113-isdc-p1-lessons-cheat-sheet-joy-ride](F:\learning\udacity\intro_to_self_driving_car\concepts\videos\1. introduction to bayesian thinking\2 joy ride\nd113-isdc-p1-lessons-cheat-sheet-joy-ride.png)

gggg