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
whiteNoise.connect(context.destination);
~~~~

### Pink Noise

Create a pink noise generator and route it to the output:

~~~~ {.javascript}
var context = new webkitAudioContext();
var pinkNoise = context.createPinkNoise();
pinkNoise.connect(context.destination);
~~~~

Modulate a sawtooth oscillator with filtered pink noise:

```javascript
var context = new webkitAudioContext();
var pinkNoise = context.createPinkNoise();
var pinkGain = context.createGainNode();
var pinkFilter = context.createBiquadFilter();
pinkGain.gain.value = 100;
pinkFilter.frequency.value = 1.618;
pinkNoise.connect(pinkFilter);
pinkFilter.connect(pinkGain);

var saw = context.createOscillator();
saw.type = saw.SAWTOOTH;
saw.frequency.value = 440.0;
var sawGain = context.createGainNode();
sawGain.gain.value = 0.3;

saw.start(0);
saw.connect(sawGain);
pinkGain.connect(saw.frequency);
sawGain.connect(context.destination);
```

### Brown Noise

Create a brown noise generator and route it to the output:

~~~~ {.javascript}
var context = new webkitAudioContext();
var brownNoise = context.createBrownNoise();
brownNoise.connect(context.destination);
~~~~

Modulate the brown noise amplitude to simulate the sound of the ocean:

```javascript
var context = new webkitAudioContext();
var brownNoise = context.createBrownNoise();
var brownGain = context.createGainNode();
brownGain.gain.value = 0.3;
brownNoise.connect(brownGain);

var lfo = context.createOscillator();
lfo.frequency.value = 0.1;
var lfoGain = context.createGainNode();
lfoGain.gain.value = 0.1;

lfo.start(0);
lfo.connect(lfoGain);
lfoGain.connect(brownGain.gain);
brownGain.connect(context.destination);
```

  [the post on Noisehack]: http://noisehack.com/generate-noise-web-audio-api/
