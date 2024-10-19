java c
CSSE2010/CSSE7201AVR Project
Semester 2, 2024 - Version 1.01 (06/10/2024)
Due: 4:00pm, Friday 25th October
Weighting: 20% (100 marks)
Clariﬁcations and changes since the initial release of the project speciﬁcation are in red.
ObjectiveAs part of the assessment for this course, you are required to undertake an AVR project which will test  you  against  some  of  the  more  practical  learning  objectives  of  the  course,  namely  your  C programming skills applied to the ATmega324A microcontroller.You  are  required  to  modify  a  program  to  implement  additional  features.  The  program  is  a  basic template of the game “Sokoban”  (described in detail on page 3) and has very basic functionality. It will present a start screen upon launch, respond to push button presses or a terminal input “s”/“S” to start the game, then display the ﬁrst level which contains a map of game objects and a ﬂashing player icon. You can add features such as moving the player, game logic, pausing, audio etc. The various features have diﬀerent levels of diﬃculty and will each contribute a certain number of marks.
Don’t PanicWhile this is a long project speciﬁcation, there’s not actually that much code to write! You’ve been provided with approximately 2000 lines of code to start with! You are not expected to fully understand all of the provided code, and several intro/getting started videos are available on Blackboard, which contains a demonstration of some of the expected functionality to be implemented and walks through setting the project up with the provided base code, as well as how to submit.
Grading NoteAs described in the course proﬁle, if you do not score at least 10% on this AVR project (before any penalty) then your course grade will be capped at a 3  (i.e., you will fail the course). If you do not obtain at least 50% on this AVR project (before any penalty), then your course grade will be capped at a 5. Your AVR project mark (after any penalty) will count 20% towards your ﬁnal course grade.
This project has 17 features, broken into three tiers, and marks are distributed as follows:
Available Marks  Max Mark
Tier A
54
50
Tier B
34
30
Tier C
24
20

112
100This  means  if you  implement  all  features of tier  A  and  score  full  marks  for  each  feature, you will receive 54 marks, however it will be capped at 50 when the grade of your project is calculated. This also means that you do not need to score full marks for each feature to be able to achieve 100% for the project.
Code Style. and Restrictions
There  is  no  restriction  on  your  code,  as  long  as  your  code compiles  with  Microchip Studio installed on the lab computers. No marks are awarded nor deducted in the marking criteria forcode style, however you are advised to follow a good code style. for your own beneﬁt and to make it easier  for  course  staﬀ to  assist you. You  may  freely  create  and  add  .c/ .h ﬁles,  as well  as  include additional header ﬁles (eg: string.h, ctype.h) from the C Standard Library to any source ﬁle using #include.
You may use any C language feature (e.g., switch statements, structures, pointers), provided that they are C99 compliant and supported by the GCC compiler used by Microchip Studio.
Provided CodeYou have been provided with some base code as a starting point for this project. You should import the base code ﬁles into a project, and you will be working on adding features to the provided base code.  There  is  a  documentation  of the  base  code  on  Blackboard  which  you  should  read  prior  to implementing the features and refer to while working on the project. A setting up video on Blackboard shows how to create a new project and get the base code up and running.
Sokoban DescriptionThis AVR project involves creating a replica of the classic game “Sokoban”.  Sokoban  is  a  classic  puzzle video  game  in which the player pushes boxes around in a warehouse, aiming to get them to designated storage locations.There are 4 main object types in a game of Sokoban – player, wall, box and target. The player and boxes are movable, while walls and targets are not. In the original game, the player may push a boxin 4 directions – left, right, up and down, provided that there is no wall or other boxes behind the box. 2 boxes cannot be pushed together. The player can move to empty or target squares, but not to walls or boxes (boxes can be pushed, but player and box can never coexist on the same square). The level is complete when all boxes have been pushed onto the targets by the player. The number of boxes is always equal to the number of targets.
For this AVR implementation, the warehouse is represented using the 16x8 LED matrix:
Figure 1: Snapshot of a sample game, showing all game objects in action.
The ﬂashing player icon is rendered in this document as matrix ﬂashes between dark green and black. Likewise,
, meaning that particular pixel of the LED means a pixel which ﬂashes between dark
green and red (i.e., player on a target).
Initial OperationThe provided program has very limited functionality. It will display a start screen (see Figure 2) which detects the rising edge on the push buttons B0, B1, B2 and B3, as well as the input terminal character “s”/“S”. Pressing any of these will start a game of Sokoban and take you to the initial game board as illustrated in Figure 3.
Figure 2: Start screen on the LED matrix (scrolling) and on the terminal.Once started, the provided program is capable of detecting a rising edge on the push button B0, but no action when the button is pressed  (this will need to be implemented as part of the Move Player with Push Buttonsfeature). 
Figure 3: Initial game board after starting the game.
Terminal LayoutThe terminal used for marking will have 80 columns and 24 rows, and you are advised to keep this in mind when implementing the project. During gameplay, a message area one row in height is deﬁned on the terminal, for displaying messages. 
Figure 4: Recommended in-game terminal layout.
Wiring AdviceWhen completing this AVR project, you will need to代 写CSSE2010/CSSE7201 Semester 2 2024 AVR ProjectProlog
代做程序编程语言 make additional connections to the ATmega324A microcontroller to implement particular features. To do this, you will need to choose which pins to make these connections to. There are multiple ways to do this, so the exact wiring conﬁguration will be left up to you, and you must communicate this using your submitted feature summary form (on Blackboard).
Some connections are deﬁned for you in the provided base code and are shown in grey in the following table.
Wiring Table
Port
Pin 7
Pin 6
Pin 5
Pin 4
Pin 3
Pin 2
Pin 1
Pin 0
A








B
SPI connection to LED matrix
Button B3
Button B2
Button B1
Button B0
C








D






Serial RX
Serial TX
Baud rate: 19200
Program FeaturesMarks will be  awarded  for  features  as  described  below.  Part  marks will  be  awarded  if part of the speciﬁed functionality is demonstrated. Marks are awarded only on demonstrated functionality in the ﬁnal submission – no marks are awarded for attempting to implement the functionality, no matter how much eﬀort has gone into it, if there is no evidence of functionality when the program is run. You may implement higher-tier features without implementing all lower-tier features if you like (subject to prerequisite  requirements).  The  number  of marks  is  not  an  indication  of diﬃculty.  Marks  may  be deducted if features interact negatively with one another or aﬀect gameplay experience.
You may modify any of the code provided and use any of the code from learning lab sessions and/or posted on the course Blackboard site.
Minimum Performance                              Pass/FailYour program must have at least the features present in the code supplied to you, i.e., it must build on Microchip Studio and run, show the start screen, and display the initial game when a push button or “s”/“S” is pressed. No marks can be earned for other features unless this requirement is met, i.e., your AVR project mark will be zero.
Start Screen                                    Tier A: 4 marksModify the program so that when it starts  (i.e., the AVR microcontroller is reset) it outputs your name and student number to the serial terminal, in the indicated location  (remove the placeholder text, including the chevrons <>). Do this by modifying the function start_screen in ﬁle project.c.
Move Player with Push Buttons                           Tier A: 6 marksThe  provided  program  does  not  allow  moving  the  player.  Modify the  program  so that when  push button B0  (connected to port B pin 0) is pressed, the player moves right.  Similarly, pressing push button B1 (connected to port B pin 1) should move the player down, push button B2 (connected to port B pin 2) should move the player up, and push button B3  (connected to port B pin 3) should move the player left.If the player would be moved oﬀ the LED matrix display, it must wrap around to the other side of the display. For example, if the player is on the far-right side of the LED matrix, then pressing B0 must move the player to the  far-left side of the LED matrix  (same is true for up/down). Whenever the player is moved, the ﬂashing cycle of the player icon must be reset, such that the player icon instantly displays dark green and remains dark green for 200ms. The player should move when the button is pressed; no behaviour is expected when the button is released, nor if the button is held down.If the player is moved onto a target, the target must ﬂash between dark green and red (). When the player  is  moved  oﬀ the target, the target  must  revert to  displaying  solid  red. You  do  not  have to consider moving onto walls or boxes until the later Game Logic – Walls and Game Logic – Boxes features, respectively.
Move Player with Terminal Input            Tier A: 6 marksThe provided program does not register any terminal inputs once the game has started. Modify the program so that pressing “w”/“W” moves the player up, and “a”/“A”, “s”/“S”, and “d”/“D” move the player left, down, and right, respectively, in a similar manner to the previous task. Note that both the lowercase and uppercase versions of each letter must execute these movements as described. Also, note that the inbuilt serial functionality handles keyboard inputs that are held down for you.Just like in the previous task, the player must wrap around the edges, and the ﬂashing must be reset whenever the player moves. Holding down a key will usually send multiple instances of that key to the terminal. Unlike the push buttons, this means holding down a key will result in the player repeatedly moving, which is ﬁne and to be expected. 
Game Logic – Walls                          Tier A: 6 marks
RequiresMove Player with Push ButtonsorMove Player with Terminal.When the player attempts to move onto a wall, nothing should happen, and a message must be printed to the message area of the terminal telling the player that they’ve hit a wall. Below is an example of moving to the right onto a wall.
Figure 5: Example of player moving to the right and hitting a wall. This is only one example; you
must consider the player hitting walls after moving up, left and down as well.Given how often people run into walls, the message displayed must be randomly chosen from at least three diﬀerent messages. You may decide on the messages to use; however, they must clearly indicate that  the  player  has  hit  a  wall,  and  the  order  in  which  the  messages  are  displayed  must  be  non- deterministic (random).As with the player movements, if the player is on the far-right side of the LED matrix, and there is a wall on the far-left side of the LED matrix, and the player moves to the right, they would hit the wall on the far-left side, and the move would be considered invalid. The same goes for all the other edges.
Figure 6: Example of player moving to the right and hitting a wall after wrapping around. This is only one example; you must consider hitting walls after wrapping around in other directions too.





         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
