<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cognitive Pattern Explorer</title>
    <style>
        :root {
            --bg-calm: linear-gradient(135deg, #e0f2f1 0%, #e8f5e9 100%);
            --card-calm: rgba(255, 255, 255, 0.85);
            --text-calm: #2e4f4f;
            --accent-calm: #4db6ac;
            --accent-hover-calm: #00897b;

            --bg-stress: linear-gradient(135deg, #eceff1 0%, #cfd8dc 100%);
            --card-stress: rgba(255, 255, 255, 0.9);
            --text-stress: #263238;
            --accent-stress: #ff7043;
            --accent-hover-stress: #d84315;

            --transition-speed: 0.4s;
            --radius: 16px;
            --shadow: 0 8px 32px rgba(0, 0, 0, 0.08);
        }

        @media (prefers-reduced-motion: reduce) {
            * {
                animation: none !important;
                transition: none !important;
            }
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            background: var(--bg-calm);
            color: var(--text-calm);
            transition: background var(--transition-speed), color var(--transition-speed);
            overflow-x: hidden;
        }

        body.stress-mode {
            background: var(--bg-stress);
            color: var(--text-stress);
        }

        .container {
            width: 100%;
            max-width: 700px;
            background: var(--card-calm);
            backdrop-filter: blur(10px);
            border-radius: var(--radius);
            padding: 40px;
            box-shadow: var(--shadow);
            transition: all var(--transition-speed);
            position: relative;
            min-height: 450px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        body.stress-mode .container {
            background: var(--card-stress);
        }

        .screen {
            display: none;
            animation: fadeIn 0.5s ease forwards;
            flex-grow: 1;
        }

        .screen.active {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1, h2, h3 {
            margin-bottom: 20px;
            font-weight: 600;
            text-align: center;
        }

        p {
            margin-bottom: 25px;
            line-height: 1.6;
            text-align: center;
            font-size: 1.1rem;
        }

        /* Buttons & Modes */
        .mode-container {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 30px;
        }

        button {
            padding: 14px 28px;
            border: none;
            border-radius: 30px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s ease;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }

        button:focus-visible {
            outline: 3px solid currentColor;
            outline-offset: 2px;
        }

        .btn-calm {
            background-color: #4db6ac;
            color: white;
        }
        .btn-calm:hover { background-color: #00897b; transform: translateY(-2px); }

        .btn-stress {
            background-color: #ff7043;
            color: white;
        }
        .btn-stress:hover { background-color: #d84315; transform: translateY(-2px); }

        .btn-next {
            background-color: #37474f;
            color: white;
            align-self: center;
            margin-top: 20px;
        }
        body.stress-mode .btn-next { background-color: #ff7043; }

        /* Progress Bar */
        .progress-container {
            width: 100%;
            background: rgba(0,0,0,0.05);
            height: 6px;
            border-radius: 3px;
            margin-bottom: 30px;
            display: none;
        }
        .progress-bar {
            height: 100%;
            width: 0%;
            background: #4db6ac;
            border-radius: 3px;
            transition: width 0.3s ease;
        }
        body.stress-mode .progress-bar { background: #ff7043; }

        /* Chapter 1 Options */
        .options-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
            width: 100%;
        }
        .option-btn {
            background: rgba(255,255,255,0.6);
            border: 1px solid rgba(0,0,0,0.08);
            text-align: left;
            border-radius: var(--radius);
            padding: 18px;
            color: inherit;
            box-shadow: none;
        }
        .option-btn:hover {
            background: rgba(255,255,255,0.9);
            transform: translateX(5px);
        }

        /* Drag and Drop Lists */
        .drag-container {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 20px 0;
        }
        .draggable-item {
            background: white;
            padding: 16px;
            border-radius: 10px;
            border: 1px dashed #ccc;
            cursor: grab;
            display: flex;
            align-items: center;
            gap: 15px;
            user-select: none;
            transition: background 0.2s;
        }
        .draggable-item:active { cursor: grabbing; }
        .draggable-item.dragging { opacity: 0.5; background: #f5f5f5; }
        .drag-index {
            background: rgba(0,0,0,0.05);
            width: 28px;
            height: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            font-size: 0.9rem;
            font-weight: bold;
        }

        /* Results / Charts */
        .result-item {
            margin: 20px 0;
        }
        .result-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
            font-weight: 500;
        }
        .result-bar-bg {
            background: rgba(0,0,0,0.05);
            height: 12px;
            border-radius: 6px;
            overflow: hidden;
        }
        .result-bar-fill {
            height: 100%;
            width: 0;
            background: #4db6ac;
            transition: width 1s cubic-bezier(0.1, 1, 0.1, 1);
        }
        body.stress-mode .result-bar-fill { background: #ff7043; }

        .journal-box {
            background: rgba(255,255,255,0.5);
            border-left: 4px solid #4db6ac;
            padding: 20px;
            border-radius: 0 var(--radius) var(--radius) 0;
            margin-top: 25px;
            font-style: italic;
        }
        body.stress-mode .journal-box { border-left-color: #ff7043; }
    </style>
</head>
<body>

    <div class="container">
        <!-- Progress Indicator -->
        <div class="progress-container" id="progressContainer">
            <div class="progress-bar" id="progressBar"></div>
        </div>

        <!-- Start Screen -->
        <div class="screen active" id="screenStart">
            <h1>Cognitive Pattern Explorer</h1>
            <p>Welcome. Explore your thinking styles, decision loops, and cognitive habits through a series of light interactive mental experiments.</p>
            <p style="font-size: 0.9rem; opacity: 0.8;">Choose an environmental mode to begin:</p>
            <div class="mode-container">
                <button class="btn-calm" onclick="setMode('calm')">Calm Mode</button>
                <button class="btn-stress" onclick="setMode('stress')">Stress Mode</button>
            </div>
        </div>

        <!-- Chapter 1: Scenarios -->
        <div class="screen" id="screenCh1">
            <h3 id="ch1Title">Chapter 1: The Situation</h3>
            <p id="ch1Question">Loading scenario...</p>
            <div class="options-list" id="ch1Options"></div>
        </div>

        <!-- Chapter 2: Priorities Draggable -->
        <div class="screen" id="screenCh2">
            <h3>Chapter 2: Core Priorities</h3>
            <p>When starting a completely new project under uncertainty, how do you prioritize? Drag and reorder them from highest priority (1) to lowest (4).</p>
            <div class="drag-container" id="ch2DragList"></div>
            <button class="btn-next" onclick="submitCh2()">Lock Priorities</button>
        </div>

        <!-- Chapter 3: Timeline Mapping -->
        <div class="screen" id="screenCh3">
            <h3>Chapter 3: Thinking Sequence</h3>
            <p>When solving an unexpected, urgent obstacle, what order do your thoughts typically arrive in? Arrange from first action to last.</p>
            <div class="drag-container" id="ch3DragList"></div>
            <button class="btn-next" onclick="submitCh3()">Generate Profile</button>
        </div>

        <!-- Reflection Journal / Final Results -->
        <div class="screen" id="screenFinal">
            <h2>Your Reflection Journal</h2>
            <p>Based on your exploratory flow, here is an educational glimpse into how you navigate thought processes.</p>
            
            <div id="chartsContainer"></div>

            <div class="journal-box" id="journalFeedback">
                Loading insights...
            </div>

            <button class="btn-next" onclick="restartApp()">Explore Again</button>
        </div>
    </div>

    <script>
        // --- Data Models ---
        const tendencies = {
