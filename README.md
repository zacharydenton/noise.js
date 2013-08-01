noise.js
========

noise.js is a library that provides noise generators for the Web Audio
API. Currently, noise.js provides generators for white noise, pink
noise, and brown noise.

Read [the post on Noisehack][] for details and a demo.

Usage
-----

### White Noise

Create a white noise generator and route it to the output:

~~~~ {.javascript}
var context = new webkitAudioContext();
var whiteNoise = context.createWhiteNoise();
whiteNoise.connect(audioContext.destination);
~~~~

### Pink Noise

Create a pink noise generator and route it to the output:

~~~~ {.javascript}
var context = new webkitAudioContext();
var pinkNoise = context.createPinkNoise();
pinkNoise.connect(audioContext.destination);
~~~~

### Brown Noise

Create a brown noise generator and route it to the output:

~~~~ {.javascript}
var context = new webkitAudioContext();
var brownNoise = context.createBrownNoise();
brownNoise.connect(audioContext.destination);
~~~~

  [the post on Noisehack]: http://noisehack.com/generate-noise-web-audio-api/
