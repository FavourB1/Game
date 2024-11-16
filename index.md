<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>P5.js Centered Game with Background</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.6.0/p5.min.js"></script>
  <style>
    /* Center canvas on the page */
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
    let ball = {
      x: 500,
      y: 500,
      size: 50,
      dx: 4,
      dy: 3,
      color: '#ff6347'
    };

    let bgImage;

    function preload() {
      // Load the background image
      bgImage = loadImage('afro.png');
    }

    function setup() {
      // Create a centered canvas
      let cnv = createCanvas(1000, 1000);
      cnv.parent('body');
    }

    function draw() {
      // Draw the background image
      background(bgImage);

      // Draw a bouncing ball
      fill(ball.color);
      ellipse(ball.x, ball.y, ball.size);

      // Update ball position
      ball.x += ball.dx;
      ball.y += ball.dy;

      // Bounce off edges
      if (ball.x - ball.size / 2 < 0 || ball.x + ball.size / 2 > width) {
        ball.dx *= -1;
      }
      if (ball.y - ball.size / 2 < 0 || ball.y + ball.size / 2 > height) {
        ball.dy *= -1;
      }
    }

    function mousePressed() {
      // Change ball color on click
      ball.color = color(random(255), random(255), random(255));
    }
  </script>
</body>
</html>

