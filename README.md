# KDC-Goals

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bucket Filling Based on Actual Percentage</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #f0f0f0;
      margin-top: 50px;
    }

    .bucket-container {
      position: relative;
      width: 200px;
      height: 400px;
      border: 2px solid #000;
      background-color: #e0e0e0;
      margin: auto;
      overflow: hidden;
    }

    .water {
      position: absolute;
      bottom: 0;
      width: 100%;
      background-color: #00f;
      transition: height 1s ease;
    }

    .percentage {
      font-size: 24px;
      margin-top: 20px;
    }

    .controls {
      margin-top: 20px;
    }

    input[type="number"] {
      padding: 8px;
      font-size: 16px;
      width: 60px;
      margin-top: 10px;
    }

    button {
      padding: 10px 15px;
      background-color: #4CAF50;
      color: white;
      font-size: 16px;
      border: none;
      cursor: pointer;
      margin-top: 10px;
    }

    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>

  <h1>Bucket Filling Based on Actual Progress</h1>

  <div class="bucket-container">
    <div class="water" id="water"></div>
  </div>

  <div class="percentage" id="percentage">0%</div>

  <div class="controls">
    <label for="progress">Enter progress percentage (0-100):</label>
    <input type="number" id="progress" min="0" max="100" value="0">
    <button onclick="updateProgress()">Update Progress</button>
  </div>

  <script>
    // Function to update the bucket based on actual percentage
    function updateProgress() {
      // Get the user input progress percentage
      const progress = parseInt(document.getElementById('progress').value);

      // Ensure the value is within the valid range (0 to 100)
      const validProgress = Math.min(Math.max(progress, 0), 100);

      // Calculate the height of the water based on the progress percentage
      const waterHeight = (validProgress / 100) * 400; // Bucket height is 400px
      document.getElementById('water').style.height = `${waterHeight}px`;

      // Update the displayed percentage
      document.getElementById('percentage').innerText = `${validProgress}%`;
    }

    // Optional: Automatically call updateProgress on page load if you want to initialize
    // updateProgress(); // Uncomment if you want to set an initial value on load
  </script>

</body>
</html>
