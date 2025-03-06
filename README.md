<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Walls</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to right, #2c3e50, #4ca1af);
            color: white;
            text-align: center;
        }
        .container {
            padding: 50px;
        }
        h1 {
            color: #ff6680;
        }
        .image-section img {
            max-width: 100%;
            border-radius: 10px;
            margin-top: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .eink-temp-container {
            display: flex;
            justify-content: center;
            gap: 50px;
            margin-top: 30px;
        }
        .eink-section, .temperature-section, .calendar-section {
            width: 30%;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }
        .eink-display, .temperature-display-box, .calendar-display {
            width: 200px;
            height: 100px;
            background: white;
            margin: 20px auto;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: black;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
        }
        .color-options button {
            margin: 5px;
            padding: 10px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        .toggle-btn {
            padding: 10px 20px;
            background: #ff6680;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>SMART WALLS</h1>
        <div class="image-section">
            <img src="image.png" alt="Smart Living Space">
        </div>
        <div class="eink-temp-container">
            <div class="eink-section">
                <h2>E-Ink Display</h2>
                <div class="eink-display" id="einkDisplay">E-Ink Display</div>
                <button class="toggle-btn" onclick="toggleEInk()">Turn Off</button>
                <h3>Select Color:</h3>
                <div class="color-options">
                    <button style="background: black; color: white;" onclick="changeColor('black')">Black</button>
                    <button style="background: gray; color: white;" onclick="changeColor('gray')">Gray</button>
                    <button style="background: white; color: black;" onclick="changeColor('white')">White</button>
                    <button style="background: blue; color: white;" onclick="changeColor('blue')">Blue</button>
                    <button style="background: red; color: white;" onclick="changeColor('red')">Red</button>
                </div>
            </div>
            <div class="temperature-section">
                <h2>Temperature Display</h2>
                <div class="temperature-display-box" id="temperatureDisplay">Temperature Display</div>
                <button class="toggle-btn" onclick="toggleTemperature()">Turn Off</button>
                <p class="temperature-display" id="temperature">Loading...</p>
            </div>
            <div class="calendar-section">
                <h2>Calendar</h2>
                <div class="calendar-display" id="calendarDisplay">Calendar</div>
                <button class="toggle-btn" onclick="toggleCalendar()">Turn Off</button>
            </div>
        </div>
    </div>
    <script>
        function toggleEInk() {
            let display = document.getElementById('einkDisplay');
            let button = document.querySelector('.eink-section .toggle-btn');
            if (display.style.background === 'white') {
                display.style.background = 'black';
                display.style.color = 'white';
                button.textContent = 'Turn On';
            } else {
                display.style.background = 'white';
                display.style.color = 'black';
                button.textContent = 'Turn Off';
            }
        }
        function changeColor(color) {
            let display = document.getElementById('einkDisplay');
            display.style.background = color;
            display.style.color = color === 'white' ? 'black' : 'white';
        }
        function updateTemperature() {
            let tempC = (Math.random() * 15 + 20).toFixed(1);
            let tempF = (tempC * 9/5 + 32).toFixed(1);
            document.getElementById('temperature').textContent = `${tempC}°C / ${tempF}°F`;
        }
        function toggleTemperature() {
            let display = document.getElementById('temperatureDisplay');
            let button = document.querySelector('.temperature-section .toggle-btn');
            if (display.style.display === 'none') {
                display.style.display = 'block';
                button.textContent = 'Turn Off';
            } else {
                display.style.display = 'none';
                button.textContent = 'Turn On';
            }
        }
        function toggleCalendar() {
            let display = document.getElementById('calendarDisplay');
            let button = document.querySelector('.calendar-section .toggle-btn');
            if (display.style.display === 'none') {
                display.style.display = 'block';
                button.textContent = 'Turn Off';
            } else {
                display.style.display = 'none';
                button.textContent = 'Turn On';
            }
        }
        setInterval(updateTemperature, 3000);
        updateTemperature();
    </script>
</body>
</html>
