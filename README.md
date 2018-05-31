# finalProj

# Project Title and purpose

The title of this project is Choose Your Own Java. The purpose of this game is to entertain and challenge the player to make the right decisions. The game also challenges the player because some of the best decisions bring you right back to the beginning of the program. This project helped me understand how if statements work and how different screens with buttons work. Last year in code studio, making new screens was very simple. This year, we had to actually write the code to switch screens. 

### Difficulties or opportunities you encountered along the way.

The toughest part was creating the story line of the adventure. It was tricky because I needed to think of something from scratch that was original. I had a great time doing it though because I love being creative and there are not many oppertunities to be creative in school these days.

### Most interesting piece of your code and explanation for what it does.
The most interesting peice of code is the massive block of text that sits right in the middle. It looks intimidating when you look at it but its very simple. It is basically a println that is told were to print based on the button pressed.
```Java
PVector buttonSize = new PVector (150, 30);

int levelNumber;

String textForMyLevel [];
String buttonOneText [];
String buttonTwoText [];
int playerChoice; 

void setup ()
{
  size (1024, 768);

  levelNumber = 0;
  playerChoice = 0;
  textForMyLevel = new String [9];
  textSize(12);

  textForMyLevel[0] = "You lift your head up from a deep sleep. BOOM! You're awake! You frantically look around. Water is your first priority. \n Its dry. So dry that your lips are cracking and your mouth feels dusty. \n To the left you can see a watering hole. To the right you see a cave. \n Go ahead and choose your own adventure.";
  textForMyLevel[1] = "The watering hole is busy. Not with other people, with other predators. \n You can try and sneek up on the water and fill your canteen, or you could build a weapon from the forest near by and try to kill a zebra for food.";
  textForMyLevel[2] = "You enter the cave and look around. Its dark so you light a match.\n A green glow surrounds the cave, you take a few steps closer to the wall and you realize its all emerald.\n You can either fill the canteen with the valuable emerald or you can keep looking for water.";
  textForMyLevel[3] = "You Sneek into the water behind the elephants. \n You know its risky to be by such big animals but they give you the most protection from other animals ";
  textForMyLevel[4] = "Your proud of yourself. You found water and you have good protection from the elephants.\n everything is going to plan. you turn around and see an elephant foot.\n you are squished. "; 
  textForMyLevel[5] = "You turn around with your canteen filled with emeralds. There is a strange light that you notice to the right.\n Do you walk towards the light to the right or do you keep walking to the cave exit up ahead. ";
  textForMyLevel[6] = "you continue into the cave. instead of it getting colder, it starts to warm up.\n A light starts to approach you in the cave. you start to run but its no use. You are destroyed by a flow of lava.";
  textForMyLevel[7] = "You approach the light slowly and see a group of elderly men around a fire. The fire is glowing a strange purple hue. \n You can turn around or you can try and sell them the emeralds. ";

  buttonOneText = new String [9];
  buttonOneText[0] = "Water";
  buttonOneText[1] = "Fill canteen";
  buttonOneText[2] = "Keep the emerald";
  buttonOneText[3] = "continue";
  buttonOneText[4] = "Restart";
  buttonOneText[5] = "walk right";
  buttonOneText[6] = "Restart";
  buttonOneText[7] = "Sell";


  buttonTwoText = new String [9];
  buttonTwoText[0] = "Cave";
  buttonTwoText[1] = "Hunt Zebra";
  buttonTwoText[2] = "Save room for water";
  buttonTwoText[3] = "Continue";
  buttonTwoText[4] = "Restart";
  buttonTwoText[5] = "Keep going to the exit";
  buttonTwoText[6] = "Restart";
  buttonTwoText[7] = "Run";
}

void draw ()
{
  background (205, 133, 63);

  // the stuff for all levels
  rect(width/2 - buttonSize.x - 100, height - 100, buttonSize.x, buttonSize.y);
  if (!buttonTwoText[levelNumber].equals(buttonOneText[levelNumber]))
    rect(width/2 + 100, height - 100, buttonSize.x, buttonSize.y); 

  PrintMyButtonTexts();
  PrintMyLevelText();

  // stuff depending on levelNumber 
  if (levelNumber == 0)
  {
    LevelZero();
  } else if (levelNumber == 1)
  {
    LevelOne();
  } else if (levelNumber == 2) 
  {
    LevelTwo();
  } else if (levelNumber == 3) 
  {
    LevelThree();
  } else if (levelNumber == 4) 
  {
    LevelFour();
  } else if (levelNumber == 5) 
  {
    LevelFive();
  } else if (levelNumber == 6) 
  {
    LevelSix();
  } else if (levelNumber == 7) 
  {
    LevelSeven();
  }
}



void PrintMyLevelText ()
{
  textSize(15);
  text(textForMyLevel[levelNumber], 100, 100);
}

void PrintMyButtonTexts ()
{
  text(buttonOneText[levelNumber], width/2 - buttonSize.x - 100, height - 150 + buttonSize.y);
  if (!buttonTwoText[levelNumber].equals(buttonOneText[levelNumber]))
    text(buttonTwoText[levelNumber], width/2 + 100, height - 150 + buttonSize.y);
}



void mousePressed() {
  playerChoice = buttonSelection ();
}

int buttonSelection ()
{
  // default 
  int thingToReturn = 0;

  if (mouseX >= (width/2 - buttonSize.x - 100) && 
    mouseX <= (width/2 - 100) && 
    mouseY >= (height - 100) &&
    mouseY <= (height - 100 + buttonSize.y))
  {
    println ("inside the left button on X");
    if (mousePressed)
    {
      println ("mouse pressed inside the left button");
      thingToReturn = 1;
    }
  } else if (mouseX >= (width/2 + 100) &&
    mouseX <= (width/2 + 100 + buttonSize.x) && 
    mouseY >= (height - 100) && 
    mouseY <= (height - 100 + buttonSize.y))
  {
    println ("inside the right button on X");
    if (mousePressed)
    {
      println ("mouse pressed inside the right button");
      thingToReturn = 2;
    }
  }

  return thingToReturn;
}



void LevelZero ()
{
  if (playerChoice == 1)
  {
    levelNumber = 1;
  } else if (playerChoice == 2)
  {
    levelNumber = 2;
  }
  playerChoice=0;
}

void LevelOne ()
{
  if (playerChoice == 1)
  {
    levelNumber = 3;
    println("Hello from the other side");
  } else if (playerChoice == 2)
  {
    levelNumber = 0;
  }
  println ("I'm in level 1");
  playerChoice=0;
}

void LevelTwo ()
{
  if (playerChoice == 1)
  {
    levelNumber = 5;
  } else if (playerChoice == 2)
  {
    levelNumber = 6;
  }
  println ("I'm in level 2");
  playerChoice=0;
}

void LevelThree()
{
  if (playerChoice == 1)
  {
    levelNumber = 4;
  } else if (playerChoice == 2)
  {
    levelNumber = 0;
  }
  println ("I'm in level 3");
  playerChoice=0;
}

void LevelFour()
{
  if (playerChoice == 1)
  {
    levelNumber = 0;
  } else if (playerChoice == 2)
  {
    levelNumber = 0;
  }
  println ("I'm in level 4");
  playerChoice=0;
}

void LevelFive()
{
  if (playerChoice == 1)
  {
    levelNumber = 7;
  } else if (playerChoice == 2)
  {
    levelNumber = 6;
  }
  println ("I'm in level 5");
  playerChoice=0;
}

void LevelSix()
{
  if (playerChoice == 1)
  {
    levelNumber = 0;
  } else if (playerChoice == 2)
  {
    levelNumber = 0;
  }
  println ("I'm in level 6");
  playerChoice=0;
}

void LevelSeven()
{
  if (playerChoice == 1)
  {
    levelNumber = 0;
  } else if (playerChoice == 2)
  {
    levelNumber = 0;
  }
  println ("I'm in level 7");
  playerChoice=0;
}


```
This is the code that moves down the tree as decisions are made.  It gets each value from both left and right and also casts the value to a String.  If the progressions arrives at the leaf nodes, those values are printed.
## Built With

* [Processing](https://processing.org/) - The IDE used

## Authors

Jake Green

## Acknowledgments

Hat tip to the choose your own adventure books for inspiring me!
Hat tip to the internet (processing) for showing me how to make a button!
