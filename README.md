
# Lab 10
## Part  1 - Flower Bed

In this part, you will create three classes. `Flower`, `FlowerBed`, and `FlowerRunner`.

1. **`Flower`** - The `Flower` class represents a flower in the bed. 
	1. Attributes:
		1. `String species` - represents the species of flower (i.e. "Sunflower" or "Rose")
	2. Methods:
		1. `Flower(String species)` - initializes a `Flower` object with a given species
		2. A getter and a setter for `species`
		3. Overrided `toString()` method - returns `Flower{species}`

After writing the `Flower` class, you should be able to test it with Example 0 in the main. 

2. **`FlowerBed`** - The `FlowerBed` class represents a flower bed. 
	1. Attributes:
		1. `Flower[] bed` - an array representing a flower bed. If a spot is occupied by a Flower, there will be a `Flower` object in the array. If the spot is empty, it will have `null`. **Flowers cannot be planted directly next to other flowers. There must be a null object on both sides of every flower(unless it is on the end of the bed.)**
	2. Methods:
			1. `FlowerBed(Flower[] bed)` - initializes a `FlowerBed` object with a given starting bed.
			2. `FlowerBed(int number)` -  initializes a `FlowerBed` object with an empty bed of size `number`
			3. A getter and a setter for `bed`
			4. `int plantFlower(Flower f)` - attempts to plant the `Flower f` in the bed. If there is an empty space with two adjacent empty spaces, you can plant a flower there. If either of its neighbors contain a flower, you cannot plant there due to overcrowding. This method plants a flower in the first available spot without neighbors and returns its index in the array. If the flower cannot be planted, it returns -1. 
			5. `void flipBed()` - In order to get more even sun on both sides, the gardener needs to be able to flip the bed 180 degrees. This method reverses the elements in the `bed` array.
			6. Overrided `toString()` method - returns something like `FlowerBed{Flower{species}, null, ...}`

After writing the `FlowerBed` class, you should be able to test it with examples 1-4.

3. **`FlowerRunner.java`** - In `FlowerRunner` use the class provided below to test your code. 

```java
import java.io.File;  
import java.io.IOException;  
import java.util.Scanner;  
  
public class FlowerRunner {  
    public static void main(String[] args) throws IOException {  
          
        System.out.println("Example 0");  
        Flower f = new Flower("Sunflower");  
        System.out.println(f); // Flower{Sunflower}  
  
        System.out.println("\nExample 1");  
  
        Flower[] fArr = {new Flower("Daisy"), null, new Flower("Sunflower"), null, null};  
        FlowerBed flowerBed = new FlowerBed(fArr);  
        System.out.println(flowerBed); // FlowerBed{Flower{Daisy}, null, Flower{Sunflower}, null, null}  
        Flower flower = new Flower("Sunflower");  
        System.out.println(flowerBed.plantFlower(flower)); // 4  
        System.out.println(flowerBed); // FlowerBed{Flower{Daisy}, null, Flower{Sunflower}, null, Flower{Sunflower}}  
  
  
        System.out.println("\nExample 2");  
  
        FlowerBed flowerBed2 = new FlowerBed(3);  
        System.out.println(flowerBed2); // FlowerBed{null, null, null}  
        Flower flower2  = new Flower("Rose");  
        System.out.println(flowerBed2.plantFlower(flower2)); //0  
        System.out.println(flowerBed2); // FlowerBed{Flower{Rose}, null, null}  
  
  
        System.out.println("\nExample 3");  
  
        Flower[] fArr3 = {new Flower("Daisy"), null, null, null};  
        FlowerBed flowerBed3 = new FlowerBed(fArr3);  
        System.out.println(flowerBed3); // FlowerBed{Flower{Daisy}, null, null, null}  
        Flower flower3  = new Flower("Rose");  
        System.out.println(flowerBed3.plantFlower(flower3)); //0  
        System.out.println(flowerBed3); // FlowerBed{Flower{Daisy}, null, Flower{Rose}, null}  
  
  
        System.out.println("\nExample 4");  
  
        Flower[] fArr4 = {new Flower("Daisy"), null, new Flower("Daisy"), null};  
        FlowerBed flowerBed4 = new FlowerBed(fArr4);  
        System.out.println(flowerBed4); // FlowerBed{Flower{Daisy}, null, Flower{Daisy}, null}  
        flowerBed4.flipBed();  
        System.out.println(flowerBed4); // FlowerBed{null, Flower{Daisy}, null, Flower{Daisy}}  
  
    }  
}
```



## Part 2 - Mountain Climber

- `Mountain` - represents a mountain
	- Attributes
		- `name` - the name of the mountain
		- `elevation` - the elevation of the mountain
		- `climbDifficulty` - the difficultly of the ascent
	- Methods
		- `Mountain(String name, int elevation, double climbDifficulty)`
		- Getters and setters for each of the instance variables
		- Overrides `toString()` method - prints `Mountain{name, elevation, difficulty}`

- `MountainClimber`
	- Attributes
		- `Mountain[] wantToClimb` - the list of mountains the climber wants to climb
	- Methods
		- `MountainClimber(Mountain[] wantToClimb)` - initializes `MountainClimber` with the array `wantToClimb`
		- Getters and Settters
		- `mostDifficultClimb()` - returns the climb in the `wantToClimb` with the highest difficulty
		- `sortClimbLowToHigh()` - sorts the `wantToClimb` list from easiest to hardest climb using BubbleSort
		- `sortClimbHighToLow()` -  sorts the `wantToClimb` list from hardest to easiest climb using BubbleSort
		- `Mountain[] getFourteeners()` - returns an sub-array of `wantToClimb` containing only the peaks above 14,000 feet
		- Overrides `toString()` method - prints `MountainClimber{Mountain{...}, Mountain{...}, ...}`

- `MountainRunner` -  Use the main below to test your code. 
```java
public static void main(String[] args){
	
	
	Mountain[] wishlist = {new Mountain("Mount Elbert", 14440, 3.2), new Mountain("Maroon Peak", 14163, 9.1), new Mountain("Longs Peak", 14259, 8.3), new Mountain("Ormes Peak", 9727, 1.2)}
	MountainClimber climber = new MountainClimber(wishlist);
	
	System.out.println(climber.mostDifficultClimb()); // Mountain{Maroon Peak, 14163, 9.1}
	
	climber.sortClimbLowToHigh();
	System.out.println(climber.getWantToClimb()[0]); // Mountain{Ormes Peak, 9727, 1.2}
	
	climber.sortClimbHighToLow();
	System.out.println(climber.getWantToClimb()[0]); // Mountain{Maroon Peak, 14163, 9.1}
	
	Mountain[] fourteeners = climber.getFourteeners();
	System.out.println(fourteeners); // MountainClimber{Mountain{Maroon Peak, 14163, 9.1}, Mountain{Longs Peak, 14259, 8.3}, Mountain{Mount Elber, 14440, 3.2}}

}
```

## Part 3  - Wordle

Design a program to play Wordle in the terminal.
## Example

```
Welcome to Wordle!

In this game you will guess a secret 5 letter word. Each turn you will guess a 5 letter word and I will tell you if a letter is correct and in the correct location with a "*", if a letter is correct but in the wrong location with a "!", and if a letter is incorrect with a "?". 

Guess the secret word: _ _ _ _ _
Your guess: magic 
_ * _ _ !

Guess the secret word: _ A _ _ _
Your guess: caret
* * _ _ _
  
...
```


`words.txt`

```
apple
grape
table
chair
plant
brick
light
sound
sweet
bread
stone
flame
water
earth
metal
glass
sword
scale
cloud
storm
smile
laugh
dream
magic
spice
sugar
honey
wheat
sheep
zebra
tiger
eagle
shark
whale
otter
camel
lemur
rhino
panda
koala
peace
trust
faith
honor
pride
glory
unity
brave
smart
quick
candy
lemon
mango
peach
berry
melon
onion
chili
spoon
knife
plate
couch
stool
shelf
clock
radio
piano
drums
viola
flute
harps
cello
organ
banjo
trump
gongs
bells
ocean
river
creek
brook
beach
shore
coast
dunes
grass
woods
field
desks
books
notes
paper
penal
ruler
chalk
board
class
teach
learn
study
tests
quizs
marks
grade
score
point
award
medal
crown
spear
arrow
armor
boots
cloak
rings
mines
oreos
steel
brass
alums
fiber
leath
wools
white
black
green
brown
beige
ivory
amber
blues
pearl
coral
smoke
dusty
foggy
clear
sunny
rainy
frost
winds
north
south
eastn
wests
upper
lower
inner
outer
front
backs
happy
sadly
angry
scary
crazy
funny
silly
sleep
awake
tired
brisk
haste
swift
slows
crawl
jumps
hopes
walks
rides
train
plane
truck
carve
boats
ships
canoe
ferry
metro
cabin
house
tower
villa
lodge
hutsy
barns
rooms
doors
gates
fence
```

