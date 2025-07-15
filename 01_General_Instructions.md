# **Project Details**

Your task is to create challenging prompts to generate dynamic 2D and 3D physics simulations.   
Your goal is to design prompts that expose model failures.   
Then you will rewrite the model's response to produce a **Golden** **Solution** – flawless code that yields an **awesome** 2D/3D simulation\!

# **Project Workflow**

## 1\. Write A Challenging Prompt

- **Be Creative\!**  
- Include **2D/3D Physics Simulations**  
- **Must Cause Model Failure**

---

## 2\. Evaluate Model Response

- **Compile & Run Response**  
- **Check for Errors**

**Decision Point**:

- If **no model failure**, go back to step 1\.  
- If **model failure**, proceed to step 3\.

---

## 3\. Annotate Model Failures

- Identify:  
  - **What is the failure?** (choose a category)  
  - **Where (line \#)** is the failure?  
  - **How can we fix it?**  
- **Upload Video of the Error**

### Failure Categories:

- **Runtime Errors**: does not run, crashes  
- **Performance Issues**: memory leak, lags  
- **Visual Issues**: missing objects  
- **Simulation Logic Issues**: unrealistic behavior

---

## 4\. Rewrite Response

- **Fix All Issues**  
- **Create Golden Response**

---

## 5\. Upload

- **Upload Video of Animation**

# **Project Details**

| STEP | Instructions |
| :---- | :---- |
| **1\. Check all Task Specifications before anything** | **For JavaScript tasks, all scripts and imports should be done in a single HTML file, use the following template:** \<\!DOCTYPE html\> \<html lang="en"\> \<head\>     \<meta charset="UTF-8" /\>     \<meta name="viewport" content="width=device-width, initial-scale=1.0" /\>     \<title\>Simulation\</title\>     \<script async src="[https://unpkg.com/es-module-shims@1.8.0/dist/es-module-shims.js](https://unpkg.com/es-module-shims@1.8.0/dist/es-module-shims.js)"\>\</script\>     \<script type="importmap"\>     {         "imports": {}     }     \</script\> \</head\> \<body\>     \<script type="module"\>             \</script\> \</body\> \</html\> **If you are proficient in Python and come across a JavaScript task, or vice versa, feel free to skip it until you find a task in your preferred language. Types of Interactions: Object to Object:** One object interacts with another (e.g., collisions, bouncing). **Object to Environment:** An object reacts to its surroundings (e.g., gravity, wind effects, walls). **Environment to Environment:** Changes within the environment affect other elements (e.g., moving platforms, shifting terrain). |
| **2\. Write a Challenging Prompt** | Basically, each prompt should: **Follow** the task specifications, like what library to use, what objects to include, etc. You’re request for additional details in the prompt as long as the specifications are covered The prompt should **sound human**, so, for example, some basic storytelling and a conversation tone should be used in the prompt. In general, **DO NOT request units** like seconds, meters, pixels, etc. The terminology gets confusing with time. Request an **ending condition**, because, without an ending condition, we cannot ensure that the simulation is not going to break after x amount of time. Aim for **Visually Pleasing & Complex Results**, but remember that the prompt should be doable in about 2 hs |
| **3\. Evaluate Model Failure** | Execute the generated code in either your own IDE or the one provided. Here, you are looking for some kind of response failure such as: Compile time or runtime error Unrealistic simulations Instruction Following – Simulation does not do what you asked it to do **If there is no failure you must modify your prompt in Step 1 to make it more challenging** **All issues in the original model response should be written down correctly. If the original response crashes, fix the issue and see the other issues (like visual specifications or logical issues) that the response has.** |
| **4\. Annotate Model Failures and submit the First Video** | Identify the type of failure(s) you found in Step 2 according to these categories: **Failure Categories: Runtime Errors:**  code fails to run crashes/becomes unresponsive **Performance Issues:**  inefficiencies, memory leaks, lags, delays Only applies if it affects too much the user experience (like reducing the FPS to less than 10-15) **Visual Specification Issues:**  missing objects, incorrect size/shape/color **Simulation Logic Issues** unrealistic or unexpected collision/interactions/movement For each relevant Failure Category you will need to: **Explain what caused this error:** *“The error occurred due to an incorrect application of friction in the simulation. The green ball was not losing speed over time as intended.”* **Explain where the error occurred:** *“Line 67: self.x\_velocity \*= self.friction  \# This line only applies friction after wall collisions”* **Explain how to fix the error:** *“To correct the failure, ensure that friction is applied consistently to both the horizontal and vertical velocities of the balls throughout the simulation. This should be done regardless of whether the ball is in motion or has bounced off the walls. Properly adjusting the velocity with friction after each movement or collision will make the simulation behave more realistically.”* **For each model failure upload a video file demonstrating the failure IMPORTANT NOTES:** We also want visualization to be visually appealing: “Nice additions” like for example a timer on the screen or a border in a figure, if they are not requested, they should not be written as issues. All issues should be written down. The explanation does not need to be long, but should be very clear. |
| **5\. Rewrite the Response and submit the Second Video** | Rewrite the failed model response into a corrected version that **fixes the code** and produces the expected **animated output**. Rewrite should be consistent with the reported failures of the original response. **The REWRITE should be that, a REWRITE of the original model response instead of an entire new solution implemented from scratch. There shouldn’t be unnecessary changes like variable names, or unjustified changes that had not been reported among the failures of the original response.** After that, **upload a video file** demonstrating the rewrite is **free of errors** and follows all instructions in the prompt. ❌ Not all the prompt requirements are implemented Mistake: Some request/constraints in the prompt, for example, the value of some constant, some interaction, or a visual specification, are not correctly implemented in the rewrite. All values given in the prompt should be used in the rewrite, that's why it's recommended to not specify values, it's hard to keep track of them all\! All interactions that the prompt requests should be implemented, for example, friction, gravity, energy conservation upon collisions, specific patterns for some objects, etc. Aspects like motion blur, background, or visual details of real objects (parachutes with the strings and the human form), if requested in the prompt, should be implemented. Asume that real objects like parachutes/mills/nets should be visually "realistic". ❌ Poor Code Quality Mistake: The code has issues with the number of comments, repeats/calculates multiple times some aspects, or in general does not follow good programming practices. All comments should have enough comments so that it is easy to follow (At least one for each major part of the logic) Some redundancies, like checking multiple times if a collision occurs between the same objects, unnecessary calculations, or repeated sections of the code should be avoided. Some good practices, like implementing functions (if necessary), should be followed. Mistake: Under certain conditions/edge cases (especially with interactive simulations), something goes wrong. Make sure that you run the simulation multiple times and test multiple cases.For example, if some parts of the code use random values, test the extreme cases, and make sure that if a position of an object is random, no overlapping is possible or at least it can be handled correctly. For interactions, test all the possible user inputs to make sure that they are correct and assess how "easy" it is to control them (they should not be hard or not intuitive to use) |

 

# **Checklist ✓**

## Prompt

| Criteria | Good Prompt | Bad Prompt |
| :---- | :---- | :---- |
| **Unambiguous** | Has a clear and singular meaning.  It is easily understood and you can make a mental picture of what the animation should look like.  **If part of the prompt is ambiguous, that particular part can’t be the issue of the model response.** A prompt can be considered unambiguous but without specifying every detail regarding its objects and/or interactions (it could not specify  objects colors, sizes or initial speeds as long as it can be understood what a desired animation would look like). **As a rule of thumb, if you can read the prompt and make a good picture of what if it’s being asked, the prompt is correct.** | Open to multiple interpretations, to the point where there are no reasonable assumptions that will lead to an appropriate code solution. Too vague or poorly defined.  Could lead to essentially different answers depending on how it's understood.  **Does not specify an ending.** |
| **Output Format** | Provides clear instructions for the desired response format, including instructions that request **visually pleasing aspects** and specify an **ending condition**. | Doesn't specify a desired output format.  Leaves the model with too much freedom in how it responds.  Ask for a very plane simulation. |
| **Human Format** | The prompt should sound natural, not like a shopping list of requirements | Sounds like: “Create a 2D simulation that does this… and this… and this….” |
| **Tasks Specifications** | The tasks should implement all tasks specifications. | Is unrelated to the specifications of the task. |

# **Golden response**

| Criteria | Good Tool Code | Bad Tool Code |
| :---- | :---- | :---- |
| **Code Correctness** | The code is free of errors and runs without issues.  Adheres to the syntax and conventions of the programming language. | Contains syntax errors, logical errors, or other issues that prevent it from running correctly. |
| **Code Conciseness** | The code is efficient and avoids unnecessary complexity.  Uses the fewest lines of code possible while remaining readable. **The code should be properly commented.** | The code is overly complex, redundant, or inefficient. Uses more lines of code than necessary. |
| **Output Correctness** | The code produces the expected output. The output is accurate and complete. | The code produces incorrect or incomplete output.  The output does not meet the task requirements. |
| **Instruction following** | The code should follow and implement ALL requirements and look good. | Some requirements are not implemented or at least incorrectly.  Like overlapping when detecting collisions. |

# **Model response issues**

| Criteria |  |  |
| :---- | :---- | :---- |
| **All issues are correctly categorized** | All issues are correctly categorized.  If there’s a runtime issue, all other issues should also be categorized. | Some issues are not written down, like some visual aspects or logical requests. |
| **There are no incorrect issues or “nice additions” marked as issues** | Remember that all issues should actually be present and affect the model response. Also, “nice additions” like for example a timer in the screen or a border in a figure, if they are not requested, they should not be written as issues, even if you later implement them in the rewrite. |  |
| **The explanation is too vague/nonsensical** | The explanation does not need to be long, but it should be clear and correct. |  |

 

# **Examples**

## ✅ Good Examples

| Example \#1 |  |
| :---- | :---- |
| **Query** | I want to create a basic game related to fishes for my computer science end of term project. But I’m not sure how to do it completely. Could you help me with a 2d animation in Python for me? It should consist of a fish tank with 20 small fish moving at random speeds and directions, colliding elastically with each other and the tank's walls. Additionally, a net controlled by the mouse should be included; each time it contacts a fish, it should capture it, becoming its container and increasing in size as more fish are caught. The simulation ends when all the fish are inside the net. |
| **Output Generated** | \[ screenshot of a good looking python game\] |

| Example \#2 |  |
| :---- | :---- |
| **Query** | I am working on creating a 3D animation in JavaScript where a large sphere performs pure rolling motion along the X-axis on a flat floor. Inside this sphere, a smaller sphere (¼ of the larger sphere’s radius) performs pure rolling in an anticlockwise direction relative to the larger sphere. I want to show my animation team what this will look like for a more complex task that they need to animate for a video game we are working on. I understand the physics but need help with the coding to properly show them. The large sphere moves back and forth along the X-axis while maintaining pure rolling conditions, meaning its rotational and translational motion are coupled. The rolling speed is set to 0.01 units per frame, assuming a frame rate of 60 frames per second. The smaller sphere also obeys pure rolling constraints as it moves inside the larger sphere. The animation runs for 1800 frames before stopping. The scene has a dark gray background, a flat floor, and directional lighting to enhance visibility. Could you help with this? |
| **Output Generated** | \[ screen shot of the game well made following all guidelines \] |

## ❌ **BAD** Examples

 

| Example \#1 |  |
| :---- | :---- |
| **Query** | Write a 2D Python animation for a bouncing yellow ball within a square, make sure to handle collision detection properly. Make the square slowly rotate. Implement it in Python. Make sure the ball stays within the square. |
| **Output Generated** | \[ Ugly looking game too simple \] **FAILING OUTPUT: DO NOT SUBMIT A GOLDEN RESPONSE THAT DOES NOT MATCH THE PROMPT. Additional Note:** Try to avoid simple prompts about a ball bouncing. The project has matured and no longer needs prompts like these |

| Example \#2 |  |
| :---- | :---- |
| **Query** | Simulate a 2D simulation in Python of a swarm of 50 boids (small triangles) moving according to simple flocking rules: separation, alignment, and cohesion. The user can introduce a predator (a red triangle) by clicking anywhere on the screen. The boids will try to avoid the predator while still maintaining their flocking behavior. If the predator catches a boid, the boid disappears. The simulation ends after 10 boids have been caught or 30 seconds have passed. Add subtle motion blur to the boids for a dynamic effect. The background should be a sky with clouds to give the simulation an immersive environment. |
| **Error** | **The background color, clouds, and motion blur are all missing, despite being requested by the prompt. There is no context about the prompt, making it sound less human like** |

| Example \#3 |  |
| :---- | :---- |
| **Query** | Create a 3D JavaScript simulation using Three.js of a marble inside a table base. The user can tilt the table by dragging the mouse, causing the marble to roll according to gravity and collisions with the table walls. The entire structure is covered with a lid to prevent the marble from escaping vertically. The goal is to navigate the marble to a target hole. End the simulation when the marble reaches the target or after 30 seconds. Respond with a single HTML file with all the scripts and imports. |
| **Error** | **The marble is shown stuck inside of the table (rather than rolling on top of it), and the 3d tilting controls are extremely difficult and unintuitive to use. There is no context about the prompt, making it sound less human like.** |

| Example \#4 |  |
| :---- | :---- |
| **Query** | I’m interested in showing my students the basic physics behind helium balloons. Could you help me make a 3D JavaScript animation using Three.js of colorful balloons (35 semi-transparent spheres with string tails) floating? Balloons rise due to buoyancy and drift based on air currents. The user can adjust the wind direction and speed using keyboard controls. Balloons avoid each other. If a balloon hits the ceiling, it pops with a soft animation. End the simulation after 30 seconds or when 20 balloons have popped. Give the results in a single HTML file. |
| **Error** | **The simulation should implement camera movements, in the current state it is difficult to see what is happening.** |

| Example \#5 |  |
| :---- | :---- |
| **Query** | Simulate a field of floating cubes that gently rise and fall like they're underwater. The user can click on any cube to apply a force that pushes it away. After 10 interactions or 30 seconds, end the simulation. Use 3D Javascript and give the results in a single HTML file. |
| **Error** | **The simulation should implement camera movement, in the current state it is difficult to see what is happening. There is no context about the prompt, making it sound less human like.** |

| Example \#6 |  |
| :---- | :---- |
| **Query** | I’ve always been fascinated by the galaxies and space travel. I’ve been thinking about creating a game that has to do with space travel, but I need help doing this. Create a 3D JavaScript simulation using the p5.js library. Simulate a small solar system consisting of a sun and two orbiting planets. Each planet must have one or two orbiting moons. The user controls a small spaceship, represented by an ellipsoid, which is leaving an orange trail and is launched automatically at the start of the simulation from a distant location away from the planets, moving at a constant velocity toward the sun. The user can slightly adjust the spaceship's direction using the arrow keys. If the spaceship crashes into the sun or a planet, the simulation should end and generate an explosion animation. The camera should follow the spaceship throughout its journey. Generate your response in a single HTML file. |
| **Error** | **It's difficult to understand what's happening in the simulation. Details could be added to better represent the planets, in addition to the fact that the moon overlaps another planet.** |

# **Things to look out for**

* While failure explanations don’t need to be super long and detailed, they should not be super vague either.   
  * For example, if the model’s code produces a type error, a bad explanation would be:   
    * ❌ “The variable x is being defined as an integer.”   
  * Instead, say something like:  
    * ✅ “The function y expects x to be a string, but x is defined as an int, which causes a type error.”


* Performance issues should only be marked if the model’s animation is significantly slowed or broken due to an inefficiency in the code.   
  * If the code does something inefficient but that doesn’t affect the end result, then performance issues should not be marked.


* If you mention that you’re going to fix an issue by doing X, then you should actually be doing X.   
  * For example, if you say that you will make the animation more realistic by adding friction, then you should actually add this friction in a way that is noticeable and actually enhances the realism of the simulation.


* Basic visual logic should be followed for animations.  
  * For example, if you’re animating shooting an arrow, then the arrow should look arrow-like, and it should move in the way arrows typically move.