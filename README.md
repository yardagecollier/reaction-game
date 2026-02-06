3D Reaction Timer
A high-precision cognitive testing tool featuring a hybrid DOM/WebGL architecture.

📋 Project Overview
The 3D Reaction Timer is a portfolio project designed to demonstrate the seamless integration of high-performance 3D graphics (Three.js) with strict application logic (Vanilla JS).

Unlike standard reaction timers, this project focuses on visceral feedback. It utilizes a "visual state machine" where lighting, geometry manipulation, and procedural audio combine to create a tension-filled user experience without sacrificing millisecond timing precision.

🎥 Live Demo

[Link to your hosted GitHub Page or Vercel deployment]

✨ Key Features
Strict State Management: The application runs on a finite state machine (IDLE, WAITING, STIMULUS, FAIL, RESULT) to prevent logical errors and race conditions.

Hybrid Rendering Engine: * Background: Uses WebGL (Three.js) for high-fidelity lighting and low-poly 3D object manipulation.

Foreground: Uses semantic HTML/CSS for the HUD (Heads Up Display) to ensure text clarity and accessibility.

Precision Timing: Utilizes performance.now() for sub-millisecond accuracy, avoiding the jitter common with standard Date objects.

Procedural Audio: Generates sound effects in real-time using the Web Audio API (Oscillators), eliminating the need for external asset loading.

Performance Metrics: Tracks session statistics (Best Time, Average Time) and assigns "Gamer Ratings" based on reaction speed.

🛠 Technical Implementation
1. The Finite State Machine (FSM)

To ensure the game is bug-free (e.g., preventing users from clicking multiple times to cheat), the logic is encapsulated in a strict switch statement.

JavaScript
const STATES = {
  IDLE: "IDLE",       // Waiting for user to start
  WAITING: "WAITING", // Random delay (2-5s) active
  STIMULUS: "STIMULUS", // Go signal!
  RESULT: "RESULT",   // showing score
  FAIL: "FAIL",       // False start penalty
};

function updateState(newState) {
  // Logic handles visual transitions and state cleanup
  currentState = newState;
  switch (newState) {
    case STATES.WAITING:
      // Sets random timeout & changes 3D object urgency
      break;
    // ...
  }
}
2. Hybrid DOM + Canvas Architecture

A common pitfall in 3D web apps is rendering text inside the canvas, which hurts readability and accessibility. This project layers an absolute-positioned div (The UI Layer) over the Three.js canvas.

Benefit: Text is crisp, selectable, and responsive.

Benefit: The 3D scene handles the "Vibe" (Atmosphere), while the DOM handles the "Data."

3. Procedural Audio System

Instead of loading MP3 files (which slows down the First Contentful Paint), the app uses an AudioContext singleton to synthesize sounds.

Success Sound: A Sine wave ramping up in frequency (0.1s).

Fail Sound: A Triangle wave ramping down (0.3s).

Note: The Audio Context initializes on the first user interaction to comply with modern browser autoplay policies.

🎨 Design System: "Dark Precision"
The UI follows a strict dark-mode palette designed to reduce eye strain while maximizing the contrast of the reaction stimulus.

State	Color	Hex	Visual Meaning
Global	Void Black	#050505	Infinite depth background
Idle	Ghost White	#E0E0E0	Neutral / Ready
Wait	Coral Red	#FF4757	Tension / Warning
Go	Neo Mint	#2ED573	High-speed stimulus trigger
Result	Electric Blue	#3742FA	Data / Analysis
🚀 How to Run Locally
This project uses Vanilla JavaScript and CDN links, requiring no build steps (Webpack/Vite) for immediate testing.

Clone the repository:

Bash
git clone https://github.com/yourusername/reaction-timer.git
Open the file: Simply open index.html in any modern web browser.

(Optional) Live Server: For the best experience, use an extension like "Live Server" in VS Code to serve the file.