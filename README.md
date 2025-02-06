# IMGD-03

Code link: https://editor.p5js.org/zx1998120/sketches/4Yg7l0jIY

Basic Visual Elements:

1.Single pulsing circle centered on screen

2.Color controlled by horizontal mouse position

3.Smooth size animation using sine wave


Inspiration:
I was thinking of creating an audio related to pattern size. When you move your mouse, it will change the size of the pattern, which also changes the audio.

The circle will continuously pulse while generating musical tones when it reaches its largest size. The piece creates an interactive relationship between position, color, and sound while maintaining minimal code complexity.

# Code:

       let circleSize = 0;
       let synth;

       function setup() {
       createCanvas(600, 600);
       colorMode(HSB, 360, 100, 100);
       noStroke();
  
       // Simple sound setup
       synth = new p5.MonoSynth();
       }

       function draw() {
       background(0);
  
       // Calculate pulse with sine wave
       let pulse = sin(frameCount * 0.1) * 100;
       circleSize = 100 + pulse;
  
       // Mouse controls color and sound
       let hue = map(mouseX, 0, width, 0, 360);
       let volume = map(mouseY, 0, height, 0, 0.5);
  
       // Draw pulsing circle
       fill(hue, 80, 80);
       ellipse(width/2, height/2, circleSize);
  
       // Trigger sound when circle reaches max size
       if (circleSize > 190) {
       playNote(hue, volume);
          }
             }

       function playNote(hue, vol) {
       let freq = map(hue, 0, 360, 200, 800);
       synth.play(freq, vol, 0, 0.1);
           }
