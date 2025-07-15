# Newton Buffet Reviewer Guide 🌟

- Do not grade tasks on their ability to cause model failure  
- move away from classic mechanics to more natural situations and minigame, so tasks only have limited (or no) physics involved (some collision would be enough)  
- If an issue is reported in the wrong category, count that as a non-failing issue, (⅗)

# **Purpose**

This guide helps reviewers identify and prevent the most common interactive simulation failures, based on internal QC feedback and real examples from Newton Buffet tasks. It includes a checklist to ensure simulations do not break due to missed or faulty user interaction handling.

# **Table of Contents**

1. Updates  
   * Change Log  
   * Important Updates  
2. Workflow  
   * Checklist: How to best look for errors  
3. Scoring Rubric  
   * Guidelines  
   * Prompts  
   * Model Failure Categories Annotation  
   * Rewrite Rubric  
4. Understanding Common Interaction Failures  
1. Interactivity Continues After End Condition  
2. Input Doesn't Trigger Any Response  
3. Unstable Behavior from Rapid Input  
4. Edge Input Cases Not Handled  
5. Timing and Interaction Conflicts  
6. Interaction Implementation Missing Despite Prompt

# **Workflow**

Follow the general workflow below when reviewing tasks:

1. Start  
2. Evaluate Prompt  
3. Bad Prompt  
   1. Yes  
      1. Flag as bad prompt, submit  
   2. No  
      1. Comfortable with subject matter?  
         1. Yes  
            1. Skip Task  
      2. Fix all issues | Grade original task (scoring rubric)  
         1. Submit  
            1. End

## **Checklist: How to best look for errors**

1) ### **Read the prompt, and make sure you understand what it is being requested.**

   

2) ### **Compile the rewritten code. ALWAYS RUN IT to check for runtime errors, do not stick with watching the video.**

     
* Does the code follow all of the prompt explicit (or sometimes implicit) instructions? If not, we know that the code needs improvements.  
* A code that does not satisfy the prompt's requirements is the first thing that a person reviewing the task will note.  
* **HELP YOURSELF WITH:**   
  * prompt\_eval    
  * response\_eval  
* Remember that, although being a great tool, the evals can raise both false positives and false negatives. They can be redundant too. In the end, it is up to your own judgment.  
* **The Evals are not always able to detect runtime errors.**  
* The Evals are really good at identifying missing documentation, comments in spanish, unused variables, redundant code

—--------------------------------------------—--------------------------------------------

**NOTE:** Although some animations may seem to be good, there might be some situations where there is a failure that can only be seen after taking a slightly deeper dive.  For example many codes have a randomness component, so there might be issues that do not always show up if the animation is only seen once.

Interact with environments to see if edge cases happen.   
Examples of this would be: 

* If objects are bouncing inside a box, does anything odd happen when they hit a corner?   
* If there is a slider to modify a parameter of the animation in an interactive task, move the slider to the extremes to see if everything works properly.

Similarly, try mixing things in the case of multiple sliders.

**EXAMPLE:**

Prompt: Create a visually appealing JavaScript program simulating 3D cloth draped over a complex 3D model (like a statue or geometric shape). Implement physics for realistic folding and collision handling. Apply an interesting texture to the cloth and add subtle wind animation. Render in a 3D canvas.

**Failing Issue of the rewritten response:** Turning the stiffness all the way down and then resetting the animation causes the ball to poke through the cloth in some places.

 If there are walls/boundaries in the animation, does it contradict (explicitly or implicitly) the prompt? Is it OK for objects to go (or not) through walls/boundaries.

3) ### **Compile the model response code. ALWAYS RUN IT, do not stick with watching the video.**

   Does it compile? If not, check if the RUNTIME ISSUES have been flagged. Also, debug it so that other issues can be detected.

4) ### **Compare the output of the model response with the prompt.**

* Make a list of all the issues that can be identified by watching the animation of the model response.   
* This should be an informal list for you to compare with the reported failure categories.   
* That way, you won't forget any of the issues that you saw.   
* Be sure of running the animation multiple times so that you detect everything that can be visually detected (without having to go through the lines of code).

5) ### **Comparison of issues:**

* This might be the most tedious part, but at the same time almost the most important one (as long as the rewritten code does not need any fixes). **You will have to compare:**  
  * The failure categories reported in the task   
  * The failure categories flags given by the **category\_eval**   
  * Your own list of failures  
      
* The endgame is to have a complete and correct list of issues in the task.  
    
* One approach is to copy the **category\_eval** and your own list into a separate cell/file, and start deleting the flagged issues if you see they had been marked in the task. If you see they weren't, and you consider them valid issues, add them\!  
    
* Do not forget to **check that all issues are under the correct category** (there is always confusion between visualization and simulation logic issues)  
    
* As always, remember that *the Eval is not perfect*. It tends to overflag, and sometimes it marks that *certain things weren't flag*,. In the end, it is up to **your own judgment.**

6) ### **Compile both codes again, and compare the model response, the improved failure categories, and the model rewrite.**

* **Check if everything is OK.**   
* Sometimes there are some visual enhancements made in the rewrite relative to the model code that are not explicit issues of the original response (example: adding a gradient background).   
  * You can add those to the Visual Issues as with something like:   
    * "Not an issue perse, but the animation can be enhanced by having a gradient background";  
    * "The airplane does not resemble an airplane, it can be made longer in the horizontal direction and it could be colored grey"

7) ### **Finally, check that both videos match with their respective responses.**

* If necessary, record the code execution and upload the correct video(s).  
* Remember, if you **had to modify the rewritten code,** always upload a new video.

8) ### **Score Based on the rubric and always give qualitative feedback:** 

     
* You must provide proper feedback to the contributor about all the issues with their task. This is the only way they can improve\!

  ### **FINAL OBSERVATIONS:**

* Was the process above a little long? Yes   
* Is this process necessary? Yes   
* Are the project quality standards really high? Yes

* In the end when improving/editing a task to make it of great quality, there has to be concordance of all the task components:  
  * PROMPT   
  * MODEL\_RESPONSE   
  * FAILURE\_CATEGORIES   
  * RECOMMENDATIONS\_TO\_FIX   
  * FINAL\_REWRITE   
  * UPLOADED\_VIDEOS


# **EXAMPLES OF FAILED TASKS**

Below, we give some examples of tasks that failed the QC (quality check) for different reasons, so you keep in mind that it is really necessary to follow the above steps.

### **Example 1**

**The following task was rejected because of an issue flagged under the wrong category, and because the rewrite mentions that a drone can be moved with the arrows, when it is actually moved with WASD.**

* (note that the prompt is not human-like, but we were not checking that at the moment)

* **Prompt:** 

“””  
Make a 3D Javascript simulation of a simple room with a bookshelf. A toy drone (represented by a disk with some blades) is flying in the room. Make it so that the user can change its height and move it around. The simulation finishes after 30 seconds.  
“””

* **Rewrite animation screenshot:**  
  * Point 2 of Logical issue explanation ('The simulation only includes a bookshelf and an undefined floor plan; it doesn't draw a room.') is more suitable under Visual specification issue.   
  * \[Code Documentation\]: The code comments on line 108 mentions " Arrows Left/Right (or QE): Rotate" but left right only works with A and D keys, not the mentioned.

  ### **Example 2**

**The following task failed because of an instruction miss and because the CB uploaded the wrong video of the rewrite.**

* **Prompt (extract):** 

“””  
My nephew is a big fan of airplanes. Help me create a Python 2D game where a plane flies through a sky with clouds and dodges missiles ….. The missiles should cause the plane to explode if they hit it, and .. Since I don't want the game to be infinite, apply two conditions: if a missile hits the plane, display the message "You lost"; but if the missiles are successfully dodged for 30 seconds, display the message "You win". Regardless of whether the message is for victory or defeat, the game should close 5 seconds later.  
“””

* **FAILURE:**   
  * \[Fail \- Rewrite Explicit Instruction Miss\] "The missiles should cause the plane to explode if they hit it" \-- the plane just disappears.   
  * \[Fail \- Rewrite Video Upload Mismatch\] Unfortunately it seems the CB uploaded a video for a completely different task.

  ### **Example 3**

**The following task failed because of a wrongly implemented ending condition.**

* **Prompt (extract):** "... The animation ends after all movement ceases."

* \[Explicit Instruction Miss\] Although there is code written for it, the simulation doesn't stop in practice. When all movement has stopped, a Simulation Ended message and a Restart button should appear according to the code, but they never appear even when all movement appears to have stopped.


  ### **Example 4**

**The following task was failed because the CB suggested a recommendation, but did not implement it (the proposed recommendations need to match with the rewritten code):**

* \[Doesn't Implement Recommendations\] The model was flagged for performance issues with the recommendation being that a mesh pool be used to avoid creating meshes on-the-fly in the main animation loop, but the rewrite still creates meshes as needed when a drop is created rather than reusing mesh instances. Personally, I don't think this needed to be flagged as an inefficiency because, while it is sub-optimal, it isn't along the lines of a memory leak or change in time complexity. But, given that it was flagged, it should have been accounted for in the rewrite.

  ### **Example 5**

**The following task was an implementation of the snake game.**   
**The rewrite was perfect, but the task failed because the person did not flag that the snake did not die when biting its own tail.**  
**The Eval in the tag did not flag this issue, but this can clearly be seen by running the model code.**

* **Prompt (extract):** "Develop a snake-like 2D game animation …using Pygame … conclude exactly after 10 dots are eaten by the snake or after it collides with its tail"

* **Failing Issues:**   
  * \[Fail \- Missing Failure Explanation\] The simulation logic issues should have included a description of the incorrect logic for the game to end when the snake collides with its tail. In the first response, the model attempted to implement this on lines 95-96, but in the game itself no tail collisions were detected.

# **Scoring Rubric**

## **Guidelines**

* The lowest score a task receives in any category will be the final score of the task.  
* Difference between a 1 and a 2:   
  * A 2 is typically awarded when the contributor just got something wrong but it is obvious that some effort was put into the task.   
  * A 1 is awarded when there was little to no effort made to complete the task.  
* Difference between a 4 and 5:   
  * A task that is a 5 is a perfect task that requires no modifications.  
  * A 4 is a good quality task that requires 1 or 2 very minor fixes e.g. typos.   
* **Any obviously SPAM/LLM tasks must be rated 1\.**


## **Prompt and its Criterias**

1. ### **Use Case**

   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Prompt \- Simulation Unfeasible\]**   
           * The prompt requests something that cannot be done (e.g. a Sphere in a 2D animation).  
   * **3 (Okay):**   
     - [ ] Prompt has limited physics element involved: customer requested us to move away from classic mechanics to move natural situations and minigame, so tasks only have limited (or no) physics involved (some collision would be enough)  
   * **4-5 (Good/Perfect):**  
     - [ ] The prompt requests for Physics simulations/animation  
   * **Additional Notes:**  
     - [ ] In some cases, the prompt requests both 2D and 3D figures in the same scene. These cases are not incorrect as long as they do not place a 3D figure in a 2D space or vice versa.  
     - [ ] Detecting collisions and movement/behaviors based on interactions are valid use cases.

2. ### **Task Specification \- Coding Language**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Prompt Invalid Coding Language\]**:  
           * The prompt requests a language not assigned in the Task Specifications  
     - [ ] **\[Fail \- Prompt Does Not Mention Coding Language\]:**  
           * The prompt clearly does not follow one or more of the specifications mentioned in the Specifications Description  
   * **3 (Okay):** **N/A**  
   * **4-5 (Good/Perfect):**  
     - [ ] The prompt language requests the language assigned in the Task Specifications  
     - [ ] The prompt does not specify the language but the model uses the correct language for the task.  
   * **Additional Notes:**

3. ### **Prompt Difficulty (2D/3D)**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Prompt Incorrect Dimensionality\]**:  
           * Prompt asks for a 2D animation when a 3D animation is needed or vice versa  
   * **3 (Okay):** **N/A**  
   * **4-5 (Good/Perfect):**  
     - [ ] Prompt asks for the appropriate simulation (2D/3D)  
   * **Additional Notes:**  
     - [ ] If the prompt fails to clearly indicate if it should be 2D or 3D then that is a fail  
     - [ ] \- “Difficulty” here refers to whether a 2D animation is needed or a 3D one. Please see Simulation Complexity if the prompt is too complex.

4. ### **Prompt Clarity and Specificity**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Prompt Unclear\]**   
           * It's not clear what is being asked, the prompt is extremely difficult to follow, or is overly vague  
     - [ ] **\[Fail \- Prompt Missing Crucial Details\]**  
           * Major details are missing that are needed to answer the prompt. You can’t reasonably fulfill the request without these missing details  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Prompt Ambiguous\]** It's mostly clear what is being asked but the request could reasonably be interpreted multiple ways  
   * **4-5 (Good/Perfect):**  
     - [ ] There is little to no room for misinterpretation of the specific request  
     - [ ] **\[Non-Fail \- Prompt Requires a Minor Assumption\] (4)**:   
           * Prompt has a specific request that doesn't require more than one minor assumption to answer it  
   * **Additional Notes:**   
     - [ ] The prompts are not expected to completely describe everything about the simulations to the last detail. As long as the main task is clear \- the response can infer the details.

5. ### **Feasibility**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Prompt Impractical Request\]**  
           * Prompt contains an impractical request that can't be answered by an LLM in a single response  
     - [ ] **\[Fail \- Prompt Impossible Request\]**  
           * Prompt has at least one request that can't be fulfilled at all  
     - [ ] **\[Fail \- Prompt Conflicting Instructions\]**  
           * Prompt gives conflicting/contradicting instructions that can't be fulfilled simultaneously  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Prompt Impractical Secondary Request\]**  
           * There are multiple requests in the prompt and it's verging on being impractical for a model to answer it in a single response, but the core request of the prompt can be fulfilled with minor concessions on the secondary requests  
   * **4-5 (Good/Perfect):**  
     - [ ] The prompt is completely actionable by an LLM or chatbot  
     - [ ] The prompt contains no conflicting instructions/statements  
   * **Additional Notes:**  
     - [ ] Impossible request:  
           * Ex: "Can you create a new sorting algorithm that runs in constant time?"  
     - [ ] Impractical request  
           * Ex: "Can you give me all the code to create a social media platform like Instagram? But make it better please

6. ### **Contrived/Unnatural Prompts**

   * **1-2 (Fail):** **N/A**  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Contrived / Unnatural Prompt\]**  
           * Prompt is contrived or otherwise unnatural  
     - [ ] **\[Non-Fail \- Somewhat Contrived / Unnatural Prompt\]**  
           * Prompt is somewhat contrived or is somewhat unnatural  
   * **4-5 (Good/Perfect):**   
     - [ ] The prompt is neither contrived or unnatural

## **Model Failure Categories Annotation**

1. ### **Failure Category Selection**

   * **Field:**  
     - [ ] **Runtime errors**  
     - [ ] **Performance issues**  
     - [ ] **Visual specification issues**  
     - [ ] **Simulation logic issues**  
   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Model Failure Category Missed\]**  
           * The CB missed selecting a category/dimension that the model has issues in.   
           * Note: All the applicable categories MUST be selected, even if the code has runtime issues  
     - [ ] **\[Fail \- Model Failure Category Incorrect\]**  
           * CB incorrectly selected one of the categories (Does not apply to visual vs simulation debates.)  
           * Note: If the CB flagged issues with the model response that are not explicit requirements in the prompt, but are implicit expectations or nice-to-haves, that’s okay as long as other clearly failing issues are pointed out  
   * **3 (Okay):**  
     - [ ] **N/A**  
   * **4-5 (Good/Perfect):**   
     - [ ] CB selects all of the applicable model’s failure categories.  
   * **Additional Notes:**  
     - [ ] If an issue is reported in the wrong category, count that as **\[Non-Fail \- Miscategorized Model Failure\]**

2. ### **Failure Explanation**

   * **Field:**  
     - [ ] **Explanation \- What does this failure mean?**  
   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Contradictory Failure Explanation\]**  
           * The explanation provided contradicts the selected category  
     - [ ] **\[Fail \- Extremely Vague Failure Explanation\]**  
           * The explanation is very vague and you can’t tell what issues the CB is talking about.  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Failure Explanation Lacking Details\]**  
           * Explanation is lacking details or does not fully specify, but you can tell what issue the CB is talking about  
     - [ ] **\[Non-Fail \- Missing Failure Explanation\]**  
           * The failure explanation is **missing at least one critique** that is applicable under the selected category  
     - [ ] **\[Non-Fail \- Unfactual Failure Explanation\]**  
           * The explanation provided has some **unfactual statements**, but at least **one valid failure explanation** was pointed out  
     - [ ] **\[Non-Fail \- Miscategorized Model Failure\]**  
           * The explanation is misplaced in the **wrong category.**

   * **4-5 (Good/Perfect):**   
     - [ ] The explanation is clear and correctly interprets the failure, either mostly or completely.  
   * **Additional Notes:**  
     - [ ] If an issue is reported in the wrong category, count that as **\[Non-Fail \- Miscategorized Model Failure\]**

3. ### **Recommendation**

   * **Field:**  
     - [ ] **Recommendation to Correct the Failure**  
   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Underfixing Recommendation\]**  
           * Implementing the recommendation *does not fix the major issues with the model response*.  
     - [ ] **\[Fail \- Recommendation Unrelated to Failure\]**  
           * Recommendation *is not related to the failure explanation*.  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Recommendation Lacking Details\]**  
           * Recommendation on how to fix the issues could be *clearer and more granular*, but it’s accurate.  
   * **4-5 (Good/Perfect):**   
     - [ ] The recommendation *improves or fixes the model failure*.

4. ### **Video of Model Code Output**

   * **Field:**  
     - [ ] **Please upload a video showing the output of the model-generated code**  
   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Model Video Upload Mismatch\]**   
           * The original model code runs (doesn’t need to produce the right output), but the uploaded video *does not correspond to the code output.*  
     - [ ] **\[Fail \- Model Video Upload Missing\]**  
           * The uploaded video *doesn’t load or is missing entirely*  
   * **3 (Okay):**   
     - [ ]  **N/A**  
   * **4-5 (Good/Perfect):**   
     - [ ] The original model code runs, a video showing the code output was uploaded and corresponds to the code output.  
   * **Additional Notes:**  
     - [ ] If a “Run Time Error” is selected, uploading a video is not required.

## **Rewrite Rubric**

1. ### **Doesn’t implement recommendations**

   * **1-2 (Fail):** **N/A**  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Deviates From Recommendations\]**  
           * The rewrite response does not include the recommendation exactly as suggested but implements a similar correction that effectively addresses the failure.  
     - [ ] **\[Non-Fail \- Rewrite Ignores Recommendations\]**  
           * The rewritten code doesn’t implement at least one of the fixes recommended in the model failure annotation section  
   * **4-5 (Good/Perfect):**   
     - [ ] The rewrite response incorporates the recommendations and effectively corrects the failure.

2. ### **Video of the Improved Output**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Rewrite Video Upload Mismatch\]**  
           * The uploaded video does not correspond to the code output.  
     - [ ] **\[Fail \- Rewrite Video Upload Missing\]**  
           * The uploaded video doesn’t load or is missing entirely.  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Video Upload Variance\]**  
           * The video mostly aligns but with small variance. (e.g. a change in speed, 1 or 2 graphics, visibility of item.) It's clear the video came from the code before the final product.  
   * **4-5 (Good/Perfect):**   
     - [ ] A video of the improved code output was uploaded and corresponds to the code output from the rewritten model response.  
           

3. ### **\[Rewrite/SxS\] Clearly Worse Than Model Response**

   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Rewrite Worse than Model Response\]**   
           * **The rewrite would clearly perform worse overall across the rubric dimensions**  
   * **3 (Okay):**  
     - [ ] **N/A**  
   * **4-5 (Good/Perfect):**   
     - [ ] The updated response would clearly perform better overall across the rubric dimensions  
   * **Additional Notes:**  
     - [ ] Do not penalize an attempter/tasker for making minimal or no changes to the original response.  
           

4. ### **\[Code\] Instruction Following**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Rewrite Explicit Instruction Miss\]**  
           * 1 or more explicit instructions are not followed  
     - [ ] **\[Fail \- Rewrite Does Not Fulfill Prompt\]**  
           * The response does not fully answer the question  
     - [ ] **\[Fail \- Rewrite Uses GUI Window as Border\]**  
           * The prompt asks for a square/rectangular container, but the code incorrectly uses the GUI window itself as the square/rectangular container, rather than drawing a container  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Implicit Instruction Miss\]**  
           * All explicit instructions are clearly followed but there may be minor issues with implicit (non-mentioned) instructions  
     - [ ] **\- \[Non-Fail \- Rewrite Subjective Instruction Miss\]**   
           * Subjectively misses some aspects of fully answering the question  
   * **4-5 (Good/Perfect):**   
     - [ ] All explicit instructions are clearly followed  
     - [ ] The response fully answers the question  
   * **Additional Notes:**  
     - [ ] Only applicable to instructions in the prompt that are related to the code implementation.   
           * Ex: “Please use an iterative approach and not a recursive one”  
             

5. ### **\[Code\] Compilation**

   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Rewrite Code Execution Issues\]**  
           * The code does not compile or throws runtime errors  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Code Runtime Side Effects\]**  
           * The code runs, but has side-effects such as warnings  
   * **4-5 (Good/Perfect):**   
     - [ ] Code runs perfectly without any errors or warnings  
           

6. ### **\[Code\] Code Correctness**

   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Rewrite Code Incorrect Output\]**  
           * The rewritten code crashes during runtime  
           * The behavior of the simulation/game does not align with what the prompt asks for (ignore edge case misses)  
     - [ ] **\- \[Fail \- Rewrite Uses Simplistic Physics\]**  
           * The code uses overly-simplistic collision detection for polygons. For example, rather than using normals, just swapping the velocity vectors of objects  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Misses Edge Cases\]**  
           * We do not penalize CBs for missing certain edge cases.  
           * Given the complexity of the tasks and the 3-hour AHT, it is ok that the submitted code may not address every possible scenario.  
   * **4-5 (Good/Perfect):**   
     - [ ] The rewritten code completely solves the prompt request, correctly implementing all visual details and physical behaviors that were specified in the prompt.  
   * **Additional Notes:**  
     - [ ] The tasks include simulations or games, which can be quite time consuming to implement perfectly.   
     - [ ] When evaluating code correctness, if 90% of the behavior of the simulation/game aligns with what you'd expect and the code only misses some edge cases, that's okay. Flag it as **\[Rewrite Misses Edge Cases\].**

7. ### **\[Code\] Performance**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Rewrite Code Extremely Inefficient\]**   
           * The code implementation is extremely inefficient.   
             1. Ex: takes an O(n^3) brute force approach when it's possible to fulfill the request in O(nlogn)  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Code Moderately Efficient\]**   
           * The code implementation is moderately efficient with room for further optimization.   
             1. Ex: O(n^2) was used when O(nlogn) is possible  
   * **4-5 (Good/Perfect):**   
     - [ ] The code implementation is well-optimized, utilizing efficient algorithms and data structures wherever possible

8. ### **\[Code\] Readability**

   * **1-2 (Fail):**   
     - [ ] **\[Fail \- Unreadable Rewrite Code\]**   
           * The code is difficult to read because of poor formatting such as missing indentation, poor markdown, excessive white space, or no whitespace (minified code), etc;  
     - [ ] **\[Fail \- Misleading Rewrite Code Variable Names\]**   
           * Variable/class/method names are not indicative of their function.   
             1. Ex: a misleading variable name such as \`even\_array \= \[1, 3, 5, 7\]\`  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Poorly Formatted Rewrite Code\]**   
           * The code can be formatted better in some areas, but it's still readable

     OR

     - [ ] **\[Non-Fail \- Rewrite Code Poor Variable Names\]**   
           * Variable/class/method names don't follow the general naming conventions of the respective language  
   * **4-5 (Good/Perfect):**   
     - [ ] The code is well organized and uses consistent formatting, making it highly readable  
     - [ ] Variable/class/method names are meaningfully chosen and are reflective of their purpose

9. ### **\[Code\] Documentation**

   * **1-2 (Fail):**  
     - [ ] **\[Fail \- Rewrite Code Missing Documentation\]**  
           * No code documentation is provided explaining complex or unintuitive code logic or when the prompt asks for it  
     - [ ] **\[Fail \- Rewrite Code Misleading Documentation\]**  
           * Documentation provided doesn't align with the corresponding code (\~ unfactual)  
   * **3 (Okay):**  
     - [ ] **\[Non-Fail \- Rewrite Code Bloated Documentation\]**   
           * There is far too much documentation provided, completely bloating the code  
     - [ ] **\- \[Non-Fail \- Rewrite Code Documentation Lacking Details\]**   
           * The documentation can be slightly improved in terms of clarity or coverage, but there are enough relevant comments to explain the code, even if the comments don’t fully explain the logic  
   * **4-5 (Good/Perfect):**   
     - [ ] The documentation provided is clear and concise, adding value to each section of the code by explaining the code choices made  
     - [ ] An appropriate amount of documentation is provided.   
           * Ex: code is divided into meaningful sections and comments are added per section rather than for each line  
   * **Additional Notes:**  
     - [ ] Documentation constitutes both code comments and docstrings

10. ### **\[Code\] Safety/Security**

    * **1-2 (Fail):**  
      - [ ] **\[Fail \- Unsafe Rewrite Code\]**  
            * The response code clearly has a malicious intention (e.g., virus/malware generation, exposes personal information)  
            * The code implementation can introduce common security vulnerabilities, such as SQL Injection  
    * **3 (Okay):**  
      - [ ] **N/A**  
    * **4-5 (Good/Perfect):**   
      - [ ] The code implementation has no security or safety issues

11. ### **Simulation Code Design**

    * **1-2 (Fail):**  
      - [ ] **\[Fail \- Rewrite Low FPS Animations\]**  
            * Animations use a low frame rate (10 fps or below)  
      - [ ] **\[Fail \- Rewrite Code Unexplained Constants\]**  
            * CB defines random constants without explaining what they are (perhaps in a comment) and they’re not self-explanatory (“GRAVITY \= 0.98” is fine, but “PROPERTY\_1 \= 0.253” isn’t)  
      - [ ] **\[Fail \- Rewrite Code Unutilized Constants\]**   
            * There are 6 or more occurrences of CB defining a constant that represents a property but rather than utilizing this constant in the code, the value was hardcoded (each hardcoded instance is counted as one occurrence)  
      - [ ] **\[Fail \- Rewrite Code Highly Redundant Logic\]**  
            * Copy/pasting or repeating the code logic rather than using loops  
      - [ ] **\[Fail \- Rewrite Code Highly Redundant Logic\]**   
            * The code contains a noticeable amount of redundant logic that could’ve been placed in a helper function or a class  
              * Note: Do not overflag this.   
                * For example, if 2 or 3 lines of code is repeated twice, that’s okay. Only flag if the helper function makes sense (can be used as a blackbox) and if you’d save more than 5% of the total lines of code by replacing all the redundancies.  
      - [ ] **\[Fail \- Rewrite Terrible Code Design\]**  
            * Code implementation doesn’t adhere to design principles, making it hard to maintain/extend down the line  
    * **3 (Okay):**  
      - [ ] **\[Non-Fail \- Rewrite Subpar Code Design\]**  
            * Code implementation mostly adheres to design principles but there is room for improvement.  
      - [ ] **\[Non-Fail \- Rewrite Code Some Unutilized Constants\]**   
            * There are up to 5 occurrences of CB defining a constant that represents a property but rather than utilizing this constant in the code, the value was hardcoded (each hardcoded instance is counted as one occurrence)  
      - [ ] **\[Non-Fail \- Rewrite Code Slightly Redundant Logic\]**   
            * The code contains some amount of redundant logic that could’ve been placed in a helper function or a class, but you would save fewer than 5% of the total lines of code \-  
    * **4-5 (Good/Perfect):**   
      - [ ] None of the issues pointed out in 1-2/Fail or 3(Okay)

# **🎮 Understanding Common Interaction Failures**

Here are some common interaction failures and how to resolve them.

## **1\. Interactivity Continues After End Condition**

* **Issue:** Simulation still responds to keyboard/mouse input after its designated ending (e.g., time or event-based).   
* **Impact:** Breaks prompt logic and can trigger visual/physics issues post-finish.   
* **Prevention:**   
  * Lock input after the end condition.   
  * Visually indicate when interaction has stopped (e.g., overlay, frozen UI).

## **2\. Input Doesn't Trigger Any Response**

* **Issue:** Clicks, drags, or key presses are implemented but have no effect.   
* **Impact:** Fails user interaction requirements.   
* **Prevention:**   
  * Confirm interaction causes visible change.   
  * Log or debug input listeners.

## **3\. Unstable Behavior from Rapid Input**

* **Issue:** Spamming or holding inputs causes bugs (e.g., overlapping spawns, crashes, lag).  
* **Impact:** Makes simulation unpredictable and breaks logic.  
* **Prevention:**   
  * Throttle input handlers.  
  * Cap object generation or interactions per second.

## **4\. Edge Input Cases Not Handled**

* **Issue:** Clicking outside bounds, pressing multiple keys, or dragging to edge breaks the simulation.  
* **Impact:** Simulation crashes or behaves erratically.  
* **Prevention:**   
  * Clamp inputs to canvas boundaries.  
  * Add guards to prevent unexpected state changes.

## **5\. Timing and Interaction Conflicts**

* **Issue:** Timed events and interaction logic interfere (e.g., user presses button after state switch).  
* **Impact:** Can desync simulation phases.  
* **Prevention:**   
  * Queue or debounce late inputs.  
  * Lock input states during transitions.

## **6\. Interaction Implementation Missing Despite Prompt**

* **Issue:** Prompt requests user interaction, but code lacks handlers or logic.  
* **Impact:** Task fails instruction-following.  
* **Prevention:**  
  * Match every user action described (click, key, drag) with code.   
  * Check all prompt phrases: "user can", "on click", "using arrows", etc.

