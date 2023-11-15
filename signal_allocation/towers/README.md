# Towers

This class will maintain a set of tower objects which all have different ids, locations, signals, and powers. 

## Getting Started Steps

- running "make setup" will install correct dependencies and check for correct python version (3.7+)
- running "make clean" will clean the project by removing all "pycache" folders and files
- running "make format will run autopep8 and docformatter to auto format the code
- running "make style" will run a lint checker on your code
- running "make test" or "make" will run all unit tests that have been created
- running "make coverage" will run all unit tests and give you a code coverage report

# Tower

## Requirements

- You must include a class called "Tower" which is used in the Towers class.
- You can include any functions you find helpful alongside the ones listed below.
  
## Interface

- The initialization of the class must be Tower(self, tower_id, position, power, signal) initializes class variables with each of the passed values.
  - The tower_id is a unique identifier for this tower.
  - Position should be a tuple containing two floats between 0 and 1, representing x and y. The bounds for this world are 0 and 1.
  - The power represents how far the tower's signal carries, and is also a float between 0 and 1.
  - Signal should be a positive integer.
- To describe more about how these Tower objects are used, consider a circle going out from its position with radius power. Now imagine another tower, with a similar circle. If these two circles overlap, and these two towers have the same signal, then there is interference. This is what we are trying to avoid in this project. This is shown in the image below:

![Tower init](https://github.com/jwheelo1/Ecen4763FinalProject2023/blob/main/example_pics/random_init.png)

# Towers

## Requirements

- You must implement a class that handles the below interfaces for maintaining a group of Tower objects.
- The class name must be called "Towers".
- You must implement at least 14 unit tests.
- Must get a 10/10 when running "make style"
- Your unit tests must reach 100% code coverage

## Interface

- The initialization of the class must be Towers(self, tower_list=None, random_num_towers=10, random_min_power=0.1, random_max_power=0.2)
  -  If tower_list is not None, it contains a list of tuples, each representing a tower. The init function should use these values to initialize Tower objects corresponding to each entry in the list. You can store these how you like.
  -  The first entry in each tuple is the tower's id. The second is the position, and the third is the power. The signal should default to 0 when creating new Tower objects.
  -  example:
    ```
    [('a', (0.5, 0.75), 0.2),
    ('b', (0.4, 0.75), 0.2),
    ('c', (0.6, 0.75), 0.2)]
    ```
  -  The other parameters dictate how a random set of towers should be initialized. If tower_list is None, these parameters should be used to create a tower_list and then Tower objects in the same way as before.
  -  random_num_towers dictates the number of random towers to generate. Signal should be initialized to 0, and the position should be generated randomly from 0 to 1. The other two parameters are bounds on the tower's power. Generate a random number for power within these bounds.
- The function add_tower(self, tower_id, position, power, signal=0) adds a new tower to Towers.
- The function remove_tower(self, tower_id) removes the tower with id tower_id from Towers.
- The function get_overlaps(self) returns a list of tuples containing two towers, where (tower1, tower2) will be in the list if and only if tower1's area of coverage overlaps with tower2's area. In this case, tower1 and tower2 are both Tower objects. In the example image shown above, the list would be [(t0, t1), (t0, t3), (t1, t0), (t1, t2), (t2, t1), (t3, t0)], where t0 represents the Tower object with id 0, and so on.
- The function get_overlapping_towers(self, tower) returns a list of Tower objects whose area of coverage overlaps with tower's area of coverage. In the example image obove, get_overlapping_towers(t0) would return [t1, t3].
- The function get_towers(self) returns a list of all of the Tower objects stored in this object.
- The function get_num_objects(self) returns the number of Tower objects stored in this object
- Finally, the function visualize_towers(self) should either show an image or save an image containing a visualization of the towers in this object. I will include some examples. For this section, I will give an example implementation with MatPlotLib which you can use. I highly recommend editing this code as you please, just as long as it clearly describes the layout of the tower objects and how they overlap with eachother.

## Tests

- Test initializing from a list, make sure that all of the Tower objects are stored and created correctly.
- Test random initialization (i.e. when tower_list = None), and make sure the bounds given in the initialization are followed.
- Test that adding and removing towers works correctly, and that calling get_overlaps afterwords results in the correct list.
- Corner case: towers that touch at a single point should still be considered overlapping. Make sure this happens! (ex. [('a', (0,0), 0.5), ('b', (1,0), 0.5)]

## Example Code
```
from matplotlib.colors import colorConverter
import matplotlib.pyplot as plt
import matplotlib.cm as cm
import numpy as np

### The rest of your Towers code goes here ###

    def visualize_towers(self):
        fig = plt.figure()
        fig.set_size_inches((8,8))
        ax = plt.Axes(fig, [0., 0., 1., 1.])
        ax.set_axis_off()
        fig.add_axes(ax)
        ax.invert_yaxis()

        towers = self.get_towers()

        if len(towers) > 0:

            max_signal = max(towers, key=lambda x:x.signal).signal
            colors = cm.gist_rainbow(np.linspace(0, 1, max_signal+1))

            for v in towers:
                fc = colorConverter.to_rgba(colors[v.signal], alpha=0.3)
                c = plt.Circle(v.position,v.power,fc=fc)
                ax.add_artist(c)

        fig.savefig('test/signal_allocation/test.png')
        plt.show()
```

## Library

You can only use basic python libraries (no special imports (except for visualization this time!))
