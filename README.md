# 6th-web-tech
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web Technology Lab - Experiment 6</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #eef2f7;
            color: #1e293b;
            transition: background-color 1s;
        }

        header {
            background: #172554;
            color: white;
            text-align: center;
            padding: 25px 15px;
        }

        header h1 {
            margin: 0 0 12px;
        }

        header p {
            margin: 7px;
            font-size: 16px;
        }

        .container {
            max-width: 1000px;
            margin: 25px auto;
            padding: 0 18px;
        }

        .card {
            background: white;
            margin-bottom: 22px;
            padding: 22px;
            border-radius: 12px;
            box-shadow: 0 3px 12px #00000012;
        }

        h2 {
            color: #1d4ed8;
            margin-top: 0;
        }

        button {
            border: none;
            background: #2563eb;
            color: white;
            padding: 10px 18px;
            margin: 5px 5px 5px 0;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
        }

        button:hover {
            background: #1e40af;
        }

        #clock {
            font-size: 35px;
            font-weight: bold;
            color: #2563eb;
            margin: 12px 0;
            font-family: monospace;
        }

        #date {
            color: #64748b;
        }

        #hoverPara {
            font-size: 18px;
            padding: 15px;
            background: #eff6ff;
            border-radius: 8px;
            transition: font-size 0.2s;
            cursor: pointer;
        }

        #carTrack {
            height: 95px;
            position: relative;
            overflow: hidden;
            background: #e2e8f0;
            border-radius: 8px;
            border-bottom: 5px solid #64748b;
            margin: 15px 0;
        }

        #car {
            position: absolute;
            left: 0;
            top: 15px;
            font-size: 48px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        th, td {
            border: 1px solid #cbd5e1;
            padding: 11px;
            text-align: left;
        }

        th {
            background: #dbeafe;
        }

        .status {
            font-weight: bold;
            color: #047857;
        }

        footer {
            background: #172554;
            color: white;
            text-align: center;
            padding: 18px;
            margin-top: 30px;
        }

        @media (max-width: 600px) {
            #clock {
                font-size: 27px;
            }

            .card {
                padding: 16px;
            }

            th, td {
                padding: 7px;
                font-size: 13px;
            }
        }
    </style>
</head>

<body>

<header>
    <h1>WEB TECHNOLOGY LAB</h1>
    <p><strong>Experiment No. 06</strong></p>
    <p>JavaScript – Timer Functions and Arrays</p>
</header>

<div class="container">

    <!-- QUESTION 1: DIGITAL CLOCK -->
    <section class="card">
        <h2>1. Digital Clock</h2>
        <p>Displays the current time using the JavaScript Date object.</p>

        <div id="clock">00:00:00</div>
        <p id="date"></p>

        <p class="status">Clock updates every second using setInterval().</p>
    </section>

    <!-- QUESTION 2: DYNAMIC BACKGROUND -->
    <section class="card">
        <h2>2. Dynamic Background Colour</h2>
        <p>The background colour changes automatically every 30 seconds.</p>

        <button onclick="changeBackground()">Change Colour Now</button>
        <button onclick="resetBackground()">Reset Background</button>

        <p id="colorCode">Current Colour: #eef2f7</p>
        <p class="status">Uses setInterval() and random RGB values.</p>
    </section>

    <!-- QUESTION 3: MOUSE EVENTS -->
    <section class="card">
        <h2>3. Mouse Events – Change Font Size</h2>

        <p id="hoverPara"
           onmouseover="increaseSize()"
           onmouseout="decreaseSize()">
            Move your mouse over this paragraph to increase the
            font size. Move it away to restore the original size.
        </p>

        <p class="status">Uses onmouseover and onmouseout events.</p>
    </section>

    <!-- QUESTION 4: MOVING CAR -->
    <section class="card">
        <h2>4. Move and Stop the Car</h2>
        <p>Click Move to animate the car and Stop to stop its movement.</p>

        <div id="carTrack">
            <span id="car">🚗</span>
        </div>

        <button onclick="moveCar()">Move Car</button>
        <button onclick="stopCar()">Stop Car</button>

        <p id="carStatus" class="status">Car is ready.</p>
    </section>

    <!-- QUESTION 5: ARRAY OF STUDENT OBJECTS -->
    <section class="card">
        <h2>5. Student Array and Objects</h2>
        <p>
            Student details are displayed by iterating through an array
            of objects. Students are categorized by year of birth.
        </p>

        <table>
            <thead>
                <tr>
                    <th>S.No.</th>
                    <th>Student Name</th>
                    <th>Register Number</th>
                    <th>Year of Birth</th>
                    <th>Category</th>
                </tr>
            </thead>

            <tbody id="studentTable"></tbody>
        </table>

        <p id="studentSummary" class="status"></p>
    </section>

    <!-- DATE OBJECT -->
    <section class="card">
        <h2>JavaScript Date Object</h2>
        <p id="dateDetails"></p>
    </section>

</div>

<footer>
    <p>Web Technology Lab | Experiment No. 06</p>
</footer>

<script>
    // QUESTION 1: DIGITAL CLOCK
    function displayClock() {
        const d = new Date();

        let hours = String(d.getHours()).padStart(2, "0");
        let minutes = String(d.getMinutes()).padStart(2, "0");
        let seconds = String(d.getSeconds()).padStart(2, "0");

        document.getElementById("clock").textContent =
            hours + ":" + minutes + ":" + seconds;

        document.getElementById("date").textContent =
            d.toDateString();
    }

    displayClock();
    setInterval(displayClock, 1000);


    // QUESTION 2: DYNAMIC BACKGROUND COLOUR
    function changeBackground() {
        const red = Math.floor(Math.random() * 256);
        const green = Math.floor(Math.random() * 256);
        const blue = Math.floor(Math.random() * 256);

        const color = `rgb(${red}, ${green}, ${blue})`;

        document.body.style.backgroundColor = color;

        document.getElementById("colorCode").textContent =
            "Current Colour: " + color;
    }

    setInterval(changeBackground, 30000);

    function resetBackground() {
        document.body.style.backgroundColor = "#eef2f7";

        document.getElementById("colorCode").textContent =
            "Current Colour: #eef2f7";
    }


    // QUESTION 3: MOUSE EVENTS
    function increaseSize() {
        document.getElementById("hoverPara").style.fontSize = "28px";
    }

    function decreaseSize() {
        document.getElementById("hoverPara").style.fontSize = "18px";
    }


    // QUESTION 4: MOVE AND STOP THE CAR
    let carPosition = 0;
    let carTimer = null;

    function moveCar() {
        if (carTimer !== null) {
            return;
        }

        const track = document.getElementById("carTrack");
        const car = document.getElementById("car");

        document.getElementById("carStatus").textContent =
            "Car is moving...";

        function animateCar() {
            const maxPosition = track.clientWidth - car.offsetWidth;

            if (carPosition >= maxPosition) {
                carPosition = 0;
            } else {
                carPosition += 3;
            }

            car.style.left = carPosition + "px";
            carTimer = setTimeout(animateCar, 20);
        }

        animateCar();
    }

    function stopCar() {
        clearTimeout(carTimer);
        carTimer = null;

        document.getElementById("carStatus").textContent =
            "Car stopped at " + carPosition + " px.";
    }


    // QUESTION 5: ARRAY OF STUDENT OBJECTS
    const students = [
        { name: "John", regno: "UR13CS129", birthYear: 1998 },
        { name: "Joseph", regno: "UR13CS456", birthYear: 2001 },
        { name: "Madhu", regno: "URK24CS9035", birthYear: 2005 },
        { name: "Arun", regno: "UR24CS125", birthYear: 1999 },
        { name: "Priya", regno: "UR24CS138", birthYear: 2003 }
    ];

    const table = document.getElementById("studentTable");

    let before2000 = 0;
    let after2000 = 0;

    students.forEach(function(student, index) {
        let category;

        if (student.birthYear < 2000) {
            category = "Before 2000";
            before2000++;
        } else if (student.birthYear > 2000) {
            category = "After 2000";
            after2000++;
        } else {
            category = "Year 2000";
        }
        const row = document.createElement("tr");

        [
            index + 1,
            student.name,
            student.regno,
            student.birthYear,
            category
        ].forEach(function(value) {
            const cell = document.createElement("td");
            cell.textContent = value;
            row.appendChild(cell);
        });
        table.appendChild(row);

        console.log(
            student.name + "'s Register Number is " + student.regno
        );
    });

    document.getElementById("studentSummary").textContent =
        "Before 2000: " + before2000 +
        " | After 2000: " + after2000;

    // DATE OBJECT METHODS
    function displayDateDetails() {
        const d = new Date();

        document.getElementById("dateDetails").textContent =
            "Date: " + d.getDate() +
            " | Month: " + (d.getMonth() + 1) +
            " | Year: " + d.getFullYear() +
            " | Day (0-6): " + d.getDay() +
            " | Hours: " + d.getHours() +
            " | Minutes: " + d.getMinutes() +
            " | Seconds: " + d.getSeconds() +
            " | Timestamp: " + d.getTime();
    }

    displayDateDetails();
    setInterval(displayDateDetails, 1000);
</script>
</body>
</html>
