# **COMMON MISTAKES**

# **Overview**

This guide is designed to help contributors identify and avoid the most frequent **mistakes in the Newton Buffet project**. Each section covers a specific type of issue—ranging from misclassified errors to poor instruction adherence or flawed code rewrites.

The goal is to ensure clarity, consistency, and technical accuracy across all submitted prompts, evaluations, and golden responses. By following these best practices, you’ll improve your review quality, reduce revisions, and help maintain the overall standard of the project.

Use this as a **reference** while annotating model failures, writing rewrites, or reviewing prompt clarity—so every submission meets expectations the first time.

# **Common errors that make a task fail:**

* The prompt asks for a square/rectangular container, but the code incorrectly uses the GUI window itself as the square/rectangular container, rather than drawing a container  
* The code uses overly simplistic collision detection for polygons.   
  * For example, rather than using normals, some code samples simply swapped the velocity vectors of objects upon collision, which is incorrect.  
* Animations use a low frame rate (10 fps or below)  
* The response defines random constants without explaining what they are (perhaps in a comment)  
* The response defines constants that represent a property but are everywhere relevant, this property value is hardcoded rather than utilizing the constant  
* Copy/pasting or repeating the code logic rather than using loops  
* Code implementation uses poor design choices and lacks even the fundamental principles such as modularity, abstraction, separation of concerns, etc. It would be hard to maintain and extend this code down the line  
* The CB missed selecting a category/dimension in which the model has issues.  
  * Note: All the applicable categories MUST be selected, even if the code has runtime issues.  
  * All issues should be mentioned.  
* In general, DO NOT REQUEST UNITS.   
  * A common issue is that the prompt requests constraints like “9.8 frames (or meters)/second\*\*2”.   
    * As the frame rate is usually 60, a gravity of 9.8/(60\*\*2) could be too low, and the animation would not look natural.   
  * Asking for meters instead of frames is also confusing.   
  * In general, just say that “the objects are affected by gravity”, and that would be correct, the model should be able to reason a good value for the gravity, and in case that it is too strong or too low, then it can be pointed out as an issue and fixed in the rewrite.  
* Unclear or missing controls in interactive animations. If no controls are specified, use standard ones (e.g., arrow keys or WASD for 2D motion).  
* Low visual quality or unrealistic movement. Animations should be visually appealing and recognizable (e.g., fish should look like fish), with natural motion unless stated otherwise.  
* Missing prompt specifications in the rewrite. Ensure all original requirements are included, especially those the initial response overlooked.

---

# **❌ Common Mistakes Caught by Reviewers ❌**

## 📋 Instruction Following / Response Fulfillment

**What it means:** Some prompt instructions were skipped or misinterpreted.

**How to avoid it:**

* Highlight all requirements (e.g., duration, user interaction, behavior).  
* Verify each one is covered in the code or rewrite.

**Examples:**

| Example 1 |
| :---- |
| The prompt explicitly requests **"a continuous rain"** of spheres. |
| The total number of spheres is limited to **50**, as one falls another is generated, after a while all the spheres get stuck and no more can be spawned, so the explicit request of the prompt **is not fulfilled. ❌** |

## **🧩 Prompt Issues**

**What it means:** The prompt is vague, inconsistent, or hard to implement.  
**How to avoid it:**

* **✅ *Clarity*:** Use simple, direct language with concrete actions.  
* **✅ *Feasibility*:** Avoid overly specific or impossible setups.  
* **✅ *Consistency*:** Check for logical timing, object counts, and event flow.  
* **✅ *Natural Design*:** Avoid stacking too many unrelated features just to trick the model.

### Examples:

#### Example 1

"Give me a JavaScript code to build a 3D animation of a 3-shelf unit filled with upright books (thin boxes). At frame 0, the bottom shelf begins to tilt. **As it gives way, all books on that shelf fall, hitting the shelf above.** Some knock down more books, creating a satisfying chain reaction. End once all books have fallen or are at rest."

##### MISTAKE

* The prompt explicitly requests **"all books on that shelf fall, hitting the shelf above”**  
* **By the laws of gravity, an object cannot fall and hit an object above it, therefore, this prompt it’s not feasible ❌**

## **🗂️ Failure Category Selection (Most flagged by QC)**

- What it means: One or more failure categories were missed or incorrectly selected.  
- How to avoid it:  
  - Always check if multiple error types apply.  
  - Use the rubric as a checklist (e.g., runtime error, output issue, logic failure).

### Examples:

| Example 1 |
| ----- |
| Prompt request that the **water turns from blue to brown** after filling the washing machine. |
| After the water fills, the color doesn't change from blue to brown, "Visual specification issues" should have been selected and explained, making this task a failure. ❌ |

---

## **🧾 Failure Explanation (Most flagged by QC)**

* What it means: The explanation of the issue is vague, incorrect, or incomplete.  
* How to avoid it:  
  * Clearly describe *what* failed, *why*, and *how to fix it*.  
  * Reference specific lines or behaviors in the code.  
  * Use structured comments like: “Line 25 — gravity not applied consistently.”

### Examples:

| Example 1 |
| ----- |
| The prompt asks for an entrance at the bottom left and an exit at the top right. |
| Model response does not include the entrance and exit, which should be pointed out in the failure explanation, making this task a fail ❌ |

## 🧪 Incorrect Code Output

* **What it means:** The code runs but the simulation does not match the prompt.  
* **How to avoid it:**  
  * Recheck the prompt and confirm every object, behavior, and condition is implemented.  
  * Play through the full simulation to confirm outcomes.

### Examples:

| Example 1 |
| ----- |
| The prompt specifies that the user should be able to click anywhere to spawn a new cube block. |
| The only place blocks can be placed is along the center x-axis of the square, as if they were confined to a 2D plane in a 3D space **❌** |

---

## 📝 Code Documentation Issues

* **What it means:** The code is hard to read or lacks useful comments.  
* **How to avoid it:**  
  * Add clear comments to every major logic block.  
  * Be sure the comments are not misleading/unrelated:  
    * \[Misleading Code Documentation\]: The code comments on line 108 mentions " Arrows Left/Right (or QE): Rotate" but left right only works with A and D keys, not the mentioned.  
  * Use descriptive variable names.  
  * Eliminate duplicate or redundant code by using functions.

---

## 🧠 Chatbot Usage

**What it means:** The rewritten response or feedback includes signs of AI tool usage—like phrases such as "As an AI model..." or overly generic templated language.  
**How to avoid it:**

* Remove any AI disclaimers or meta-comments about how the solution was generated.  
* Rephrase edits using clear, specific, human-like language focused on the code and task.

**Examples:**

| Example 1 |
| ----- |
| The edited model response contained suspicious comments referring to changes made over previous versions, which may be an indicator of the use of LLMs **❌** |

---

## 🧱 Code Design Issues

**What it means:** The structure, performance, or logic of the code is flawed.  
**How to avoid it:**

* ✅ ***Readability*****:** Use consistent indentation, formatting, and naming.  
* **✅ *Performance*:** Avoid repeated calculations, laggy loops, and inefficient logic.  
* **✅ *Execution*:** Ensure the code compiles and runs smoothly.  
* 

---

### **🎥 Wrong Video Output**

**What it means:** The video doesn’t match the actual edited model response.  
**How to avoid it:**

* Double check the uploaded video to ensure your video reflects the task as described.

**Examples:**

| Example 1 |
| ----- |
| The task code was fixed by a reviewer, but omitted to upload a **new video**. |
| The video output was considerably different from the code, so the task was considered **a fail**.**❌** |

| Example 2 |
| ----- |
| **"Create a 3D animation in JavaScript. It simulates a transparent cylinder. At the bottom of the cylinder is a fan that blows air into the cylinder. The user can control the speed at which this fan spins. In the middle of the cylinder is a mesh, on top of which are objects of various shapes and weights. These objects will be affected by the force of the wind produced by the fan, causing them to float if the wind is strong enough. The simulation ends after 30 seconds. Use [Three.js](http://Three.js)."** The task requested a wind tunnel with some objects frying around. |
| The video output shows a whole different task ❌ |

# **✅ Checklist**

Use this checklist before submitting any task to ensure your evaluation and rewrite meet project standards. It covers the most common QC issues, grouped by category for speed and clarity. Taking 2–3 minutes to review these points can prevent rejections, reduce revisions, and improve the overall quality of your submissions.

## Prompt Issues

- [ ] Is the prompt clear, specific, and testable?  
- [ ] Is it feasible to implement within project scope?  
- [ ] Are object counts, timing, and logic consistent?  
- [ ] Does it avoid unnecessary complexity or unrelated features?  
- [ ] Does the prompt sound human and natural?

## Instruction Following

- [ ] Are all prompt instructions implemented (behaviors, interactions, duration)?  
- [ ] Are user interactions and event sequences correctly handled?   
- [ ] If the prompt asks for an end condition, is it correctly implemented? 

Failure Annotations 

- [ ] Are all relevant failure categories selected (including secondary ones)?   
- [ ] Is the explanation clear, with cause, impact, and fix?   
- [ ] Are specific code lines or behaviors referenced? 

Code Output 

- [ ] Does the simulation match the prompt behavior and visuals?   
- [ ] Do all physical interactions behave as expected? 

Code Issues 

- [ ] Is the code readable, well-commented, and consistently formatted?   
- [ ] Are naming conventions clear and descriptive?   
- [ ] Is code modular, efficient, and free of redundancy?   
- [ ] Does the code run without errors?   
- [ ] Is there any AI-generated phrasing, emojis or disclaimers that need to be removed?

Video Submissions 

- [ ] Does the first video clearly show the original failure?   
- [ ] Does the second video demonstrate a working fix aligned with the prompt?  
- [ ] If I improved a code that was made by another attempter, did I upload the video of the improved code running ?

