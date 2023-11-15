# Assignment 12 - Final Project

## Assignment Description

This assignment will serve as your final project for the course. It will be worth 10 percent of your grade overall, so make sure to spend plenty of time making your submission great! This assignment will be a little different from the previous ones, so make sure to read everything fully.

In this assignment you will create an algorithm for allocating radio signals to a given set of towers, such that there  is no interference between towers at any given location, i.e. towers with the same signal do not overlap in their coverage area. 

Your code will be broken up into two sections: Towers, and SignalAllocation. The Towers class maintains a group of Tower objects, each with different possible signals, locations, and powers. The SignalAllocation houses the actual algorithm you will write, which allocates signals to the different towers. Each of these parts are explained more in their respective readme files.

## Grading

- The grading is broken down into 5 sections. There is code format, your UTs, code coverage, and Solution UTs as usual.
- There is a fifth section in this assignment: a write up. This will be explained further down.
- This assignment is worth 100pts.
- The code format is worth 10 points, your UTs are worth 20, coverage is worth 20, and my UTs are worth 50.

### Write up

- There is a write up requirement for this assignment, worth 25% of your grade.
- You need to include a full breakdown of the approach you took to allocate signals, explaining your process step by step, with diagrams and examples to help illustrate this process.
- There is no limit on the length of the write up, but I will be grading based on the level of detail you go into, so please do not be too brief.
- You can use the Towers function "visualize_towers()" to make your diagrams and examples required for this section. I will include some example diagrams for you to gain inspiration from.

### Lint

- You will receive an all or nothing for lint for 7.5% of the overall grade.
- If you run `make style` and fix all errors you will get the 7.5%.
- If there are any style issues you automatically receive a 0 for this section

### Student UTs

- Your Unit Tests account for 15% of the overall grade for this assignment.
- There must be at least 28 UTs for this assignment (every UT missed is an automatic -1)
    - 14 UTs for Towers
    - 14 UTs for SignalAllocation
- All unit tests belong in the test folder and each file must begin with test i.e. (test_array.py)

### Code Coverage

- Code Coverage (the percentage of code covered by your Unit Tests) accounts for 15% of the overall grade.
- After all of your UTs are run, we will be checking the code coverage.
- The percentage of code coverage is found by running `make coverage`.

### Solution Level UTs

- Our unit tests make up the remaining 37.5% of the overall grade.
- We will run our UTs against your program.
- The percentage of our tests that pass using your code will determine your score for this section.
- You need to ensure you adhere to the 'Interface' section in each README.md to ensure you get all points.
- If you fail to adhere to the interface that will be an automatic 0 for this section (you have been warned!)e that will be an automatic 0 for this section (you have been warned!)
