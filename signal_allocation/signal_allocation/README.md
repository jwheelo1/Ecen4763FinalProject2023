# Signal Allocation Problem

Using the Towers structure, you will implement an algorithm that determines radio signals for each Tower, such that overlapping towers do not interfere with eachother, i.e. all overlapping towers should have different signals. The pictures folder shows some examples of towers with correct signal layouts, so make sure to look at those and understand what is going on.

## Getting Started Steps

- running "make setup" will install correct dependencies and check for correct python version (3.7+)
- running "make clean" will clean the project by removing all "pycache" folders and files
- running "make format will run autopep8 and docformatter to auto format the code
- running "make style" will run a lint checker on your code
- running "make test" or "make" will run all unit tests that have been created
- running "make coverage" will run all unit tests and give you a code coverage report

# SignalAllocation

## Requirements

- You must implement a class that handles the below interfaces for selecting which radio signal goes to which tower.
- The class name must be called "SignalAllocation".
- You must implement at least 14 unit tests.
- Must get a 10/10 when running "make style"
- Your unit tests must reach 100% code coverage

## Interface

- The initialization of the class must be __init__(self, tower_list=None, max_allowed_radio_signals=None, random_num_towers=10, random_min_power=0.1, random_max_power=0.2)
    - The init function should create a Towers object with the passed parameters.
    - If max_allowed_radio_signals is None, then the max number of radio signals is N, where N is the number of towers in the object you just initialized
- The function create_mapping(self), maps each tower to a signal such that overlapping towers do not share the same signal. This is where your algorithm for solving this problem needs to go.
- The function get_towers(self) should return the Towers object stored in this class.
- The function get_num_radio_signals(self), returns the number of signals used in your mapping
- The function is_valid(self), return true if create mapping was able to be solved, without running out of radio signals. If it did run out of signals, it should return false. Otherwise, this function should go through each tower in towers and make sure that it does not overlap with any towers of the same signal. 

## Tests

- Check on a variety of tower layouts, different number of towers, different sizes, special conditions.
- I will expect simple cases to be solved by your algorithm, like the small ones I have included in the pictures folder. I do not expect exactly the same behavior as mine, but for small examples, the number of signals needed should be the same.
- For large examples, the complexity of this problem really shows up. So, I do not expect your algorithm to be optimal, but it should at least produce a valid result that is close.
- Disjoint sets of towers
- Towers that meet at a single point (still considered overlapping)
- Check that your algorithm stops when it runs out of signals, and is_valid() returns false.

## Library

You can only use basic python libraries (no special imports)
