<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tire Data Visualizer</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .tire-data {
            margin-bottom: 20px;
        }
        canvas {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Tire Data Visualizer</h1>
    <form id="tire-form">
        <div class="tire-data">
            <h3>Left Front Tire</h3>
            <label>Inner Wear: <input type="number" id="lf-inner-wear"></label>
            <label>Middle Wear: <input type="number" id="lf-middle-wear"></label>
            <label>Outer Wear: <input type="number" id="lf-outer-wear"></label><br>
            <label>Inner Temp: <input type="number" id="lf-inner-temp"></label>
            <label>Middle Temp: <input type="number" id="lf-middle-temp"></label>
            <label>Outer Temp: <input type="number" id="lf-outer-temp"></label>
        </div>
        <!-- Repeat for the other tires -->
        <button type="button" onclick="visualizeData()">Visualize</button>
    </form>

    <canvas id="tireChart" width="200" height="200"></canvas>

    <script>
        function visualizeData() {
            // Get the input data
            const lfInnerWear = document.getElementById('lf-inner-wear').value;
            const lfMiddleWear = document.getElementById('lf-middle-wear').value;
            const lfOuterWear = document.getElementById('lf-outer-wear').value;

            const ctx = document.getElementById('tireChart').getContext('2d');
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['Inner', 'Middle', 'Outer'],
                    datasets: [{
                        label: 'Left Front Tire Wear',
                        data: [lfInnerWear, lfMiddleWear, lfOuterWear],
                        backgroundColor: ['red', 'orange', 'green'],
                    }]
                },
                options: {
                    scales: {
                        y: {
                            beginAtZero: true
                        }
                    }
                }
            });
        }
    </script>
</body>
</html>
