<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>P5.js Game with Clickable Zones</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.6.0/p5.min.js"></script>
  <style>
    body {
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f0f0f0;
      overflow: hidden;
    }
    canvas {
      display: block;
    }
  </style>
</head>
<body>
  <script>
    let bgImage;
    let message = ""; // Message to display when zones are clicked

    // Define interactive zones
    const zones = [
      { x: 200, y: 200, w: 100, h: 100, name: "phone", message: "The owner is studying, phone cannot be answered." },
      { x: 500, y: 200, w: 150, h: 100, name: "computer", message: "The computer is locked with a password." },
      { x: 300, y: 500, w: 120, h: 80, name: "book", message: "The book is open to a difficult chapter." }
    ];

    function preload() {
      bgImage = loadImage('afro.png'); // Background image
    }

    function setup() {
      let cnv = createCanvas(1000, 1000);
      cnv.parent('body');
    }

    function draw() {
      background(bgImage);

      // Draw interactive zones
      zones.forEach(zone => {
        noFill(); // Make zones visible for debugging
        stroke(255, 0, 0);
        rect(zone.x, zone.y, zone.w, zone.h);
      });

      // Display the clicked message
      fill(0);
      textSize(20);
      textAlign(CENTER, CENTER);
      text(message, width / 2, height - 50); // Display at the bottom of the canvas

      // Show mouse coordinates
      displayCoordinates();
    }

    function mousePressed() {
      // Check if mouse is inside any interactive zone
      zones.forEach(zone => {
        if (
          mouseX > zone.x &&
          mouseX < zone.x + zone.w &&
          mouseY > zone.y &&
          mouseY < zone.y + zone.h
        ) {
          message = zone.message; // Set the message when a zone is clicked
        }
      });
    }

    function displayCoordinates() {
      fill(255);
      textSize(16);
      textAlign(LEFT, BOTTOM);
      text(`X: ${mouseX}, Y: ${mouseY}`, 10, height - 10);
    }
  </script>
</body>
</html>
