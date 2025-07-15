# Newton Buffet– **Prompt Creation** Guide

When creating a prompt, you must ensure it is:

* It needs to **sound** “human”.  
* It needs to **cover** all the task specifications.  
* It needs to be **fully coded within approximately 2 hours and should include** a somewhat complex animation that is visually pleasing.  
* Include an end condition.  
    
* Please try to stay away from these scenarios:  
  * invoking being a kid: “As a kid”, “when I was a kid”, “Since I was young”, “Ever since I was a kid”, etc.  
  * Doing something and then getting inspired: “I was watching, reading, studying, thinking etc.”  
    *  Try to be creative\!\!  
  * Starting with a time: Yesterday, The other day, Last night, Earlier today, A few days ago

# **1\. Make It Sound Human**

When writing a prompt, please try to make it sound realistic. There isn’t a specific formula to this, but always ask yourself the question: “Does this sound like the sort of prompt I would expect a typical user would input into a chatbot?”

## **Characteristics that must not be Present in your prompt** 

* **Your response should not sound robotic:**   
  * **It should not read off like a list of commands and specifications.**   
  * Try not to start the prompt with a command. E.g. Create a 2D animation in Python within a 500px x 500px window, with a white background, featuring three concentric disks: the largest with a diameter of 400px, the smallest with a diameter of 100px. ○ It should be written in natural language and prose. Do not use bullet points  
  * Avoid repetitive phrasing like: "Create X. Then create Y. After that, do Z." **You may concisely explain why you want certain things.** And these additions might be added midway through the prompt too, not necessarily at the beginning. ○ Try to avoid frequently using terms like. “The simulation/game should” and instead use “I want it to” or “Can you make it”.  
* **Your response shouldn’t sound contrived/unnatural:**  
  * Although you want your prompts to have context for realism, do not make these sound like a story or unnecessarily verbose. As this is equally as unrealistic as sounding robotic.  
    * An example of an unnecessary lengthy context: “I used to play competitive Tetris when I was younger, can you even believe this? Time has passed by so fast. I was having lunch today and while watching some documentary about astronauts I had the best idea ever. I need your help for this one so I'm going to give you some context first. I took some courses online on python with a library called tkinter, so only use that for what I am going to ask you. Alright, here it goes: I want you to help me code a 2D tetris game. With gravity \- yes, you heard it right. Even though it sounds crazy, let me play game direction here and give you some guidelines which will make this really easy.”

  * Please try to stay away from these scenarios (they add length to the prompt without getting to the point of what the user wants/expects and are over used:  
    * invoking being a kid: As a kid, When I was a kid, Since I was young, Ever since I was a kid …  
    * Doing something and then get inspired: I was watching, reading, studying, thinking etc. Try to be creative\!\!  
    * Starting with a time: Yesterday, The other day, Last night, Earlier today, A few days ago  
* **Don’t use the same template for all your prompts:**  
  * You can vary which sentence you introduce the language specification in, which one you introduce the time limit in. You can vary where you place these (at the beginning, midway through, at the end). The 2D/3D requirement and the programming language/library don’t have to be put in the same   
    sentence.  
  * Try to avoid using this template:   
    * \[I was inspired by {event} and want to create a {type of project} using {technology}. The {project} should feature {elements/features}. The user can {action} using {controls}. The {project} ends when {ending condition}, displaying {final message}.\]  
  * **Interactiveness:**  
    * Don't say things like "Make it an interactive simulation", just say things like "I'd like to be able to control the force of shooting by holding spacebar".   
    * On the other side, clarifying that “No user interaction is needed” is OK.

## **Characteristics that you should try to have in your prompt**

* Your prompt should sound personal to make it feel more realistic.  
  * “For a college project, I want to visualize how the laws of mechanics and collisions can be used to simulate polygonal shapes bouncing and spinning in a circular container”  
  * “For my PhD research, I want to simulate a spinning galaxy…”  
  * “I’m trying to visualize how a sine wave changes over time. Can you help me animate this in Python?”  
  * I need to create a simulation of the spread of a virus to present to my medical team. Can you help…  
* **Try to talk like a normal human being would in real life.**  
  * While you want to use proper grammar and be concise, try to make your prompts sound like the sort of thing a typical human would write. That means saying things like “could you help me”

## **Avoid technical lists. Use a natural, conversational tone with a bit of story or motivation.**

### **❌ Don't write:**

***“Create a 2D animation in Python within a 500px x 500px window, with a white background, featuring three concentric disks: the largest with a diameter of 400px, the smallest with a diameter of 100px, and the middle one positioned halfway between the inner and outer disks. Each disk rotates around the same central point, but in alternating directions. Three arrows on the edge of each circle indicate the direction of rotation. The innermost disk rotates slowly in one direction, the middle disk rotates slightly faster in the opposite direction, and the outermost disk rotates the fastest, in the same direction as the first, and includes visible walls. Within this system, three balls move randomly, leaving very subtle trails and colliding with each other. When they collide, they glow and release sparks. All activity must remain confined within the walls of the outermost disk. Display the animation duration in the upper-left corner, and when the animation ends at 30 seconds, show the message "Simulation ended" just below the timer and freeze the scene.”***

### **✅ Do write:**

***“I was in my physics class, and the professor talked about rotational forces. I got the idea to implement an example that he showed in class with coding, but I think it's a little hard for me to make, so help me. I want (using Pygame, as it is the framework that I know best) three concentric disks of different radius, each rotating in a different direction (include a visual clue of where they are rotating). The more the radius, the faster they should go. I want this simulation to show rotational forces, so inside the system, three balls should be put (the balls should not escape the system, so the utmost disk should have some walls). The balls should collide with each other. Please add some subtle visual effects, like the balls leaving a little trail and a collision effect. After 30 seconds, show a "Simulation ended" message.”***

## **Tips:**

* Some basic storytelling was added (no need to dwell too much on this, just where you got the inspiration is enough)  
* The units were removed (this is very important, don’t show units please, not only because they are unnatural, but also they could lead to incorrect results/confusions, like mentioning that the system has a gravity of 9.8m/s\*\*2. Coding works with pixels or units, not meters, and frames or ticks, not seconds. Therefore, it can be confusing to determine what the model should do, and inconsistencies or out-of-scale specifications may occur. To avoid this, don’t include units in the prompt.  
* Some unnecessary details were removed. For example, it is not important to mention the direction of a rotation.  
* All the requirements are given not as a shopping list, but rather as a coherent paragraph.

# **2\. Cover All Task Specifications**

Be sure to include:

* Scenario (e.g., "Rolling Boulder Trap")  
* Objects involved  
* Programming language (e.g., JavaScript, Python)  
* **Library (e.g., p5.js, Pygame)**  
* Interaction details: Describe exactly what the user can do.

All task specifications should be requested in the prompt. This includes the scenario, objects, language, library, and whether it has interactive elements.

For the interactive elements, please clearly indicate what the user can do with the controls. Also, the camera is not considered an interaction for 3D tasks.

# **3\. Scope: Should Be Coded in \~2 Hours**

Animations, especially those in 3D, require a significant amount of time, even more so when considering potential edge cases (such as overlapping objects, failures in collision logic, handling all possible user interactions, etc.), complex dynamics, or excessive requests in the prompt.

Consider:

* Adjectives can sometimes create involuntary constraints. For example, if you mention “the background should look like a cosmic landscape,” it means that stars and possibly even planets need to be added to the simulation, which could take a while. The same applies to phrases like “vortex of particles” or similar descriptions. Keep this in consideration\!  
* The figures need to be drawn semi-realistically, which takes a while.  
* For example, drawing a person falling with a parachute, the person needs to have arms, legs, a head, etc, which can take some minutes to make. Same with cars or other things. In general, it’s okay to ask one semi-complex figure, but not more. Also, some things like fireflies, drones, and other objects can have a mostly geometrical figure (like spheres, or disks)  
* While the physics involved can be semi-realistic or somewhat simplified, please note that science concepts should be followed mostly. This can be challenging sometimes (objects floating in water need to use the buoyancy formula and follow the Archimedes principle), so don’t delve too deeply into science concepts.  
* Avoid using cloth physics, vortex, ropes, or chains, as they are hard to implement.  
* Remember that the requested animation needs to be “pretty”, so, for example, requesting trails or particle effects is correct. Same with a gradient background.  
* The animation should not be too simple, like just some balls bouncing or a single balloon flying.  
* In general, it’s better to request an end condition, mostly so that we ensure that the simulation works correctly and doesn’t break after too much time.  
* Note:  
  * **Do not** include statements like “makes things according to realistic physics" / "using realistic physics”. This makes it very difficult for a perfect task.

# **Common Issues**

* **Language awkwardness**  
  * Very unnatural, long sentences  
* **Very similar sentence length and sentence structures:**   
  * vary the sentence lengths, do not follow a similar pattern, especially when writing a bunch of prompts at a time.  
* **Very awkward inspiration / Storytelling:**   
  * Do not have to write an inspiration story if it sounds fake "I like seeing bricking falling and stacking"

Overall, make the prompt more conversational and personal and sound human.

# **Prompt Example**

## **❌ Bad Prompt Example:**

***“In Pygame, create a 2D simulation that visualizes molecules as colored circles moving in a container. Each circle represents a different type of atom (e.g., red \= oxygen, blue \= hydrogen). Atoms move with random velocities and bounce off walls and each other. When specific atoms collide with enough kinetic energy (e.g., two hydrogen atoms and one oxygen), they fuse into a new molecule (e.g., water), shown as a connected group of circles. The user can click to inject more atoms into the system. The simulation ends after 40 seconds and displays how many molecules were formed.”***

Not only is this prompt not natural enough, but it also requires a simulation that involves extensive research and chemical knowledge, which would take considerable time to implement. It could, for example, be rewritten to resemble a coding animation where balls interact and fuse based on a specific condition.

## **Examples of Prompts and how they were improved**

### **Example 1:**

“””  
**Hey\! I just got home from a trip to the Grand Canyon with my family and I honestly couldn't believe how stunning it looks. Sadly, I did not take my folding bike with me, as even though I love cycling, I did not expect it to be such a great place for that.** It made me want to recreate what the experience could've been, but using Python\! Can you help me make a 2D animation of a biker going through a **procedurally** generated road? **At work we use Tkinter, so I'm thinking we should use that.** Use a half-plane as the floor, and two circles joined by a straight line as a model to represent the bike, with maybe a handle and a seat. Implement collisions and gravity so the bike is naturally placed on top of the floor. The floor should have "gaps" or potholes where the bike can fall. The bike should have a constant velocity from left to right, and when a gap approaches, it should automatically jump, following a parabolic trajectory, dodging the holes in the road. The biker should appear to miscalculate the first jump and jump right into the first pothole, reappearing to the right of it and continuing after 2 seconds. Make it last 30 seconds, and then the simulation finishes. Thank you\!  
“””

#### **Improved/Fixed**

“””  
**I want to create a 2D animation of a biker going through a road. My idea** is to use a half-plane as the floor, and two circles joined by a straight line as a model to represent the bike, with maybe a handle and a seat. **I want the animation to look like the real thing**, so you should implement collisions and gravity so the bike is naturally placed on top of the floor. The floor should have "gaps" or potholes where the bike can fall. The bike should have a constant velocity from left to right, and when a gap approaches, it should automatically jump, following a parabolic trajectory, dodging the holes in the road. **To make it clear that the potholes are dangerous** the biker should appear to miscalculate the first jump and jump right into the first pothole, reappearing to the right of it and continuing after 2 seconds. Make it last 30 seconds, and then the simulation finishes. Thank you\! **Use the tkinter library.**  
“””

### **Example 2**

“””  
**My wife and I just came back from a trip to Brazil, and the trip was so nice it inspired us to try to create a jungle-themed screensaver for my second monitor. I sometimes use it for multitasking but most of the time it just sits there so I'd like to make a nice jungle adventure animation to display on it when I'm not using it.** **I'm most comfortable with JavaScript, so we should use the p5.js library.** Picture a lone explorer making their way across a rough terrain full of spatially scattered trails. These trails act like natural paths but they have many obstacles and branching paths. The adventurer should automatically navigate the scene, avoiding obstacles and choosing paths that lead to fewer collisions, ideally with a smooth, believable movement. The adventurer should dodge obstacles, either by moving around them or jumping over them. Use proper 3D shapes to build the environment and make the scene visually rich, but no need for the user to control anything, the movement should be handled by the program itself. The path not chosen by the adventurer should disappear to help the adventurer focus on the challenge ahead\! Let the simulation run for 30 seconds and then freeze the scene.  
“””

#### **Improved/Fixed**

“””  
**I want to create a jungle animation for my screensaver. Use p5.js.** Picture a lone explorer making their way across a rough terrain full of spatially scattered trails. These trails act like natural paths but they have many obstacles and branching paths. The adventurer should automatically navigate the scene, avoiding obstacles and choosing paths that lead to fewer collisions, ideally with a smooth, believable movement. **You can include some objects that are actually harmless, like puddles of water that create an animation when stepped on.** The adventurer should dodge obstacles, either by moving around them or jumping over them. Use proper 3D shapes to build the environment and make the scene visually rich, but no need for the user to control anything, the movement should be handled by the program itself. The path not chosen by the adventurer should disappear to help the adventurer focus on the challenge ahead\! Let the simulation run for 30 seconds and then freeze the scene.  
“””

## **✅ Good prompt Example**

Please only use these as inspiration and be creative on your own prompt writing\!   
DO NOT REUSE any of these scenarios

### **Example 1**

**I want to visualize an example of a simulation navigating somewhat unpredictable environments. Could you help me with building a 2D animation in JavaScript, using the p5.js library,** that shows a single ship automatically drifting through a crowded asteroid field. The ship should be constantly influenced by several gravity wells scattered across the space, causing its path to bend and shift in realistic physics-based ways. The asteroids should float freely and occasionally collide with each other. Try to add subtle visual effects like glowing halos around the wells and soft particle trails behind the ship. The simulation should end when the ship escapes the danger zone and display a message that says "Field cleared."

● The context sentence is short, and “unpredictable environments”/”invisible forces” are an OK hint to the model, in the scenario of space/asteroids/gravity

● The sentence requesting language/library could be shorter

### **Example 2**

I am trying to implement a p5.js simulation to mimic a stack of toy bricks wobble before tumbling over. The simulation should create many three dimensional blocks on a single base and stack them under gravity so they must obey realistic stacking balance and precision physics without any need for user interactive controls. The code should calculate collisions and resolve forces so each block settles only when it is perfectly balanced The simulation should end automatically once all blocks have remained stably stacked for ten seconds.

### **Example 3**

Sometimes it’s fun to build classic, simple games. Make a 2D jumping game using the tkinter python library. It should start by itself when the window opens, and have one player **that you can move left and right using the keyboard**. The player should also be able to jump onto platforms at different heights. **The jumps should feel realistic**, so gravity should be included. If the player falls below the bottom of the screen, the game should stop right away. **I’m trying to make something that looks and feels like old platformer games, but in a small, simple way.**

