 # Day 20 — Build an AI Face Puzzle Game 🧩

**Challenge:** AcademyBind 60-Day AI Challenge
**Difficulty:** Intermediate
**Time Spent:** ~60 min
**Deliverable:** GitHub commit URL (this file + the working HTML app)

---

## 🎯 What I Built

Aaj ka task tha apne face ko interactive puzzle game mein convert karna — webcam se live photo capture, usse grid pieces mein todna, scramble karna, aur phir drag-and-drop (mouse + touch dono) se solve karna. Saath mein timer, move counter, aur localStorage-based leaderboard bhi implement kiya.

A single self-contained `face-puzzle-game.html` file — no frameworks, no external dependencies — jo Chrome, Firefox, aur Safari mein directly chal jaata hai.

---

## ✨ Features Implemented

### 1. Camera Access
- `getUserMedia()` se front camera permission request
- Live video preview mirror effect ke saath (jaise real mirror)
- "Take Photo" button se snapshot canvas par capture
- Camera permission denied ya na milne par graceful fallback — "Upload Photo Instead" option

### 2. Puzzle Generation
- Difficulty selection: 3×3 (Easy), 4×4 (Medium), 5×5 (Hard)
- Captured face ko equal grid pieces mein slice kiya using CSS `background-position`
- Random scramble — guaranteed solvable (identity permutation reject kiya, baaki sab valid hai)

### 3. Drag & Touch Controls
- Mouse drag (desktop) aur touch drag (mobile/tablet) dono support
- Drop hone par dono pieces ka position swap hota hai
- Nearest grid cell par snap-to-grid
- Drag karte waqt pink/accent border highlight
- Correct position par green border automatically

### 4. Timer & Move Counter
- Puzzle start hote hi timer chalu (format: `mm:ss.t`)
- Live move counter
- "Placed X / Total" indicator real-time update hota hai

### 5. Win Detection & Results
- Saare pieces correct hone par auto-detect
- Timer turant stop
- Results overlay: final time, total moves, difficulty
- Top 5 best times localStorage mein save (date, time, moves, difficulty ke saath)
- Leaderboard display gold/silver/bronze ranking ke saath

### 6. UI & Polish
- Dark, modern gradient theme
- Fully responsive — desktop aur mobile dono par smooth
- Retake Photo / Play Again / New Photo / Change Difficulty buttons

---

## 🛠️ Tech Stack

- Pure HTML5 + CSS3 + Vanilla JavaScript
- `getUserMedia()` Web API for camera
- Canvas API for image capture
- `localStorage` for leaderboard persistence
- Mouse Events + Touch Events for cross-device drag support
- Zero external libraries — single self-contained file

---

## 🧠 Key Learnings

- **CSS `background-position` trick** ek hi image se multiple puzzle pieces render karne ka efficient tareeka hai — har piece apna correct slice background-position se dikhata hai, koi extra image cropping ki zarurat nahi.
- **Solvability guarantee**: Sliding-15-puzzle jaisa parity issue yahan nahi aata kyunki pieces "lift and place" karte hain (sliding nahi), to koi bhi random permutation (except identity) directly solvable hai.
- **Touch vs Mouse event unification**: Dono ke liye same core logic (`dragTo`, `endDrag`) reuse karna code duplication kam karta hai aur maintain karna easy banata hai.
- **Responsive board resizing**: Window resize par grid aur pieces ko recalculate karna zaroori tha taaki mobile rotation ya different screen sizes par layout na toote.
- **Graceful permission handling**: Camera access deny hone par turant fallback (file upload) dena UX ke liye critical hai — warna user stuck reh jaata.


*Part of the AcademyBind 60-Day AI Challenge — Day 20/60* 🚀
