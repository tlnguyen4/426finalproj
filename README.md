### Introduction
For our COS 426 final project, we were inspired by the game Guitar Hero, which is a music rhythm game in which players use a game controller to simulate playing rock music songs on a guitar.

## Goal
We decided to create a game called Song Hero, where the user clicks on different 3D shapes that pop up on the screen in a certain order. Each time the user clicks on a 3D shape in the right order, a piano note is played. The user’s goal is to guess the name of the song from the list of six choices as soon as possible. If the user successfully guesses the song, they can move on to the next round where they will have to play and guess a different song. If the user fails to guess the song, they will need to redo the round until they successfully guess the song.
The target audience for this game is individuals who enjoy playing browser games, particularly music rhythm games. 
Previous Work

There are other games such as Guitar Hero that plays the song in the background and user has to tap or tap and hold on the notes at a specified time during the song in order to score maximum points. There are also other games such as Piano Tap that plays the music as the user taps on the screen, and the goal of the game is to go as long as possible without missing a tap. 
Approach

We used JavaScript, Three.js, and Tone.js. Three.js is a JavaScript library used to create and display 3D computer graphics in a modern web browser. Tone.js is a JavaScript library use to play interactive music in a modern web browser.
Initially, we implemented the game using 2D shapes rather than 3D shapes. We created a canvas and inserted the element into the document body to display the computer graphics. We used three.js to generate random 2D circles and squares on the screen and used Tone.js to associate each shape with a note from the song. Random colors are assigned to each shape. Later on, we replaced the 2D shapes with 3D shapes and used the three.js Scene and Raycaster. We found the piano notes for various songs from the Internet.

Initially, we used nursery rhymes like “Twinkle Twinkle Little Star” and “Jingle Bells” as a few of the songs the user could play. However, we found that it was somewhat too easy for the user to correctly guess the song. Therefore, we added the chorus of pop songs to increase the difficulty for the user.

### Methodology
There are four main components to the game: 1) the instruction list, 2) the scene where user actually plays the game, and 3) the song guess menu. 

For the instruction list, there wasn’t much debate on making it 2D shapes on an HTML canvas. It would be most clear for the user to follow a list of static shapes in 2D than 3D. It was also more fun for the user to find the 3D equivalence of the 2D shapes. With this in mind, it would be costly to have a static scene and camera, so we decided to draw the 2D shapes on the canvas ourselves. We implemented the Shape class which stores information about the geometry of the shape (circle or square) and the color of the shape. For each shape, we implement how and where to draw the shape on the instruction canvas. We also implemented the remove method in order to erase the shape from the canvas. We did not implement the shapes to slide from one end of the canvas to the other. Since the speed of the game is dictated by how fast the user can click, it doesn’t make sense to add in another time factor to make things more complicated.

We set up the scene and camera using ThreeJS library. We initially implemented this as a 2D HTML canvas where the shapes are also 2D. The advantage of 2D is we could reuse the Shape class from instruction canvas to draw these shapes on a now bigger canvas. The disadvantage was it was a bit simple and not pretty looking. So we decided to upgrade the game component to 3D. The advantage of 3D is that ThreeJS is a well documented library that has functions for operations that we want to do. We create a Shape3D class that store the mesh of the shape, the song notes array, and the index in the array of the current note. The implemented the clicked on function of the class. If the shape that is clicked on is the shape that is supposed to be clicked, then we play the note of the shape using Tone.js, we remove the mesh from the scene. If there are still notes to be played, we render a new mesh in the scene with the next note, color, and geometry. If the shape is clicked in the wrong order, we increment the count of misclicks and don’t do anything to the shape. We make the shapes rotate randomly from each other and move along the y-axis (up and down the screen) to make it harder to detect and click on.

The song guess menu is a series of six buttons populated with five incorrect song names and the name of the current song. There wasn’t different implementations we had to consider. We knew it was easiest to make the menu a list of buttons and just attach event listener to them. We also implemented a modal that dynamically changes if the user clicks on the correct/incorrect guess. We shuffle the names that appear on the button to add another level of frustration to the user if they keep guessing wrong. There was not anything we did not implement for the guess menu.

### Results
Our measure of success is to have a game that perform smoothly and aesthetically pleasing. We measured our success by playing the game multiple times and tested out different scenarios to ensure the game performed as expected. For example, we tried different combinations of choosing the wrong or right song to make sure the game never breaks. We also made sure that the game doesn’t break when the user clicks on the wrong shape. As we implemented new features for our game, we made sure that the game wasn’t broken before we moved on to the next feature. That way, if we ran into any bugs, we would have an easier time identifying the source of the bug and fixing it promptly. We also played around with the colors of the shapes and the shading of the shapes’ faces so the sphere/cube does not just have one solid color. We also had friends test our game to check the game quality and ensure that there is no hidden bug on the user side.

### Discussion
The follow-up work that should be done is to allow the user to connect with their Spotify. Currently, if the user does not know the songs we have selected for our game beforehand, they will likely have a difficult time guessing the correct answer. Allowing the user to connect to their Spotify and play a song from their playlist will improve the user experience and make it more unique. The user will have a more enjoyable time playing songs that they enjoy. To import sound from the Spotify, we will need to apply a constant q transform to the audio so that it can correlate with what is occurring on the screen. We can look for a way to somehow do hand-code note-gameplay.

Neither of us had any experience with creating a 3D computer graphics game, so we learned a lot about the process of how to create a game. A lot of thought went into thinking of the game mechanics and how to use 3D computer graphics to implement these game mechanics.

We found that it was a good idea to start with 2D shapes and then move on to 3D shapes. There was a pretty big learning curve in terms of trying to implement the 3D shapes. We attempted to use code from the RayTracer assignment, but we actually found it much easier to use the RayTracer in three.js.

### Conclusion
In conclusion, we found the process of creating Song Hero very enjoyable and it was cool to see how we could use the things we learned throughout the course to create a game. Create the game also put us back to the overview of computer graphics and 3D graphical implementation. We were too focused on the assignments and how to implement the small details, and this assignment let us experiment with the existing libraries that do what we learned in class. This also give us the experience of product-thinking and make something that other people would like.
