AR Human Interaction: Multi-Gesture Demo
A lightweight, zero-dependency HTML/JS prototype demonstrating pose-driven interaction for the AR Marine Life project entry task. 

Overview
This demo utilizes Google's **MediaPipe Hands** to recognize hand gestures via the user's webcam. To demonstrate modularity and robust landmark tracking, the application detects two distinct gestures:
1. **Pinch Gesture** (Triggers a Green UI state)
2. **Victory (Peace) Sign** (Triggers a Blue UI state)

How to Run
This is a vanilla JavaScript application requiring no build tools, local servers, or package installations.

1. Clone or download this repository.
2. Double-click `index.html` file to open it in any modern web browser.
3. **Important:** Allow the browser to access your webcam when prompted.
4. Hold your hand up to the camera to test the gestures:
   * **Pinch:** Bring your thumb and index finger together.
   * **Victory:** Hold up your index and middle fingers in a "V" shape while keeping your other fingers folded.

How it Works
The application extracts 21 3D skeletal keypoints from the detected hand in real-time. 

* **Pinch Detection:** The logic isolates **Landmark 4 (Thumb tip)** and **Landmark 8 (Index finger tip)**. It continuously calculates the 2D Euclidean distance between these two points. If the distance falls below a pre-defined threshold (`0.1`), the pinch state is triggered.
* **Victory Sign Detection:** This uses spatial coordinate comparisons. Because the Y-axis originates at the top of the screen (0), a finger is "up" if its tip has a smaller Y-value than its lower joint. 
  * It checks if the Index (8) and Middle (12) fingers are extended.
  * It checks if the Ring (16) and Pinky (20) fingers are folded.
  * Finally, it calculates the Euclidean distance between the Index and Middle fingertips to ensure they are spread apart into a "V" shape, preventing false positives from fingers held tightly together.

Demo:
https://drive.google.com/file/d/1mwJocozMi0GPmvxwl-GvsNNuPwYquxee/view?usp=sharing
