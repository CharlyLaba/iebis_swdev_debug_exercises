# iebis_swdev_debugging
Source code to test debugging

## Instructions
First, *Fork* this project.

There are three exercises splitted in three branches of this repository. You must switch branches to checkout the code of each exercise.
Then, find the bugs that appear in each branch.
Fix the bugs if you can and answer to the questions proposed below.
Commit the code before checking out a different branch to avoid loosing the fixes that you have made to the code.

Once that you are done fixing bugs, *to score you must*:
1. Switch to the master branch.
2. Type below in this README.md file the answer to each question and paste some code that you have used to solve them.
3. Commit the changes
4. Push to your GitHub repository
5. Finally place a Pull Request so I can see your proposed answers


## Exercises
### Exercise 1
WorldAnalyzer is the class that holds different methods that analyzes characteristics of the word passed as argument when the object WordAnalyzer is created.

I don't know why the methods are not working properly on my laptop.Some return the correct value and others don't.

#### a) Why the method firstMultipleCharacter is returning "c" for the word comprehensive, when the correct answer should be "e"?

The firstMultipleCharacter method calls the find function which has two parameters: a char and a position value. The position value remains constant and doesn't moves forward, for that reason it stays at the first letter "c". 
    
        private int find(char c, int pos)
        {
            for (int i = pos+1; i < word.length(); i++)
            {
            
                if (word.charAt(i) == c)
                {
                    return i;
                }
            }
            return -1;
        }
    
#### b) Why the method firstRepeatedCharacter is throwing an exception?
The firstRepeatedCharacter throws a StringIndexOutOfBoundsException. 
>This means it is attempting to fetch a value that is not there. The way to fix this is by reducing the word.length method by 1 to stay within the index.
 
#### c) Why the method countGroupsRepeatedCharacters returns 3 in one case when it should be 4?
The for loop initialises "i" at value = 1 thereby ignoring the string character in position 0 which may or may not have an identical character adjacent to it. 

However, once the initial value was set to 0 it would return another StringIndexOutOfBoundsException. To circumvent this problem an additional if statement was added to test if i is equal to 0 so that it may go on to the next letter.  

*Strategy*: Place breakpoints before the methods are executed, step into them and see what happens.
### Exercise 2
In this code we are placing mines in a board game where we have several spaces that can be mined. 
The boards can contain Element objects, and since Space and Mine inherits from Element, the boards can contain this kind as well.

We have 2 boards of different **size** and **place** a different number of mines on each one.

#### a) Why placing less bombs takes longer in the second case?
The RED_BOARD is a larger int than that of the BLUE_BOARD and the values are set using the Random class. 
>Since of the constraint it is harder to randomly put the bombs in the BLUE_BOARD because the number of are almost the same to the amount of spaces there are. Randomly finding empty places to place a mine takes time.  
>On the other hand the RED_BOARD takes less time because of essentially the opposite reason, a smaller number of mines in proportion to the board size means that it is easier to randomly find a place where the mine is able to be stashed. 

#### b) Knowing that usually there are going to be more bombs than spaces in the final boards, how would you change the method minningTheBoard to be more efficient?
I don't really understand this question but I think it is more efficient to then assign every space as a bomb and then make free spaces from there. 



### Exercise 3
In this case this code looks really simple. When the "d" reaches the value **1.0**, the program should end, but it never does.

#### a) Why does not appear a message indicating that "d is 1"?
I'm not sure, but I think that it has to do with the code not exiting the **while** loop. If we were to exit the while loop then the print function would print but because it is not there and there is no error message it is only logical to assume that we remain within the while loop.

#### b) How will you fix it?
I think that decimals have a problem with java so I would just use normal int values. 

        public class Main {
            public static void main(String [] args) {
                int d = 0;
    
                while (d != 10) {
                    d += 1;
                }
    
                System.out.println("d is 1");
            }
        }

