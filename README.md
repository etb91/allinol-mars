# Abandoned, but not forgotten

**An interactive documentary about NASA's Phoenix and InSight landers on Mars.**
Made for the NASA Space Apps Challenge 2026, challenge *"Abandoned but not Forgotten: Storytelling about NASA's Discarded Equipment on the Moon and Mars"*.

**Watch it in your browser: https://etb91.github.io/allinol-mars/**

Our host is **Allinol**, a small solar-powered robot. Phoenix and InSight are its "ancestors": InSight was built on Phoenix's proven lander design, and Allinol has the same round solar panels. Allinol tells kids what the two landers were, why they were sent, what they discovered, and why they went silent.

## What's inside

**The story (about 3 minutes):**
1. **Phoenix (2007–2008).** Launch from Florida, 295 days in space, a parachute landing in the Martian Arctic, digging, and confirming water ice just below the surface.
2. **InSight (2018–2022).** Built on Phoenix's design, launched from California, landed on Elysium Planitia. It listened to more than 1,300 marsquakes and confirmed that Mars' core is liquid.
3. **The end.** Phoenix froze in the dark polar winter. Dust covered InSight's solar panels. Both landers are still on Mars today.

**Things to try on the website:**
- **Click any photo** to see what it is, when it was taken, and its NASA source.
- **Dig like Phoenix:** dig a trench, find something white, then wait 4 sols to see if it's ice or salt.
- **Then and now:** sliders comparing Phoenix's landing site (2008 vs 2017) and InSight's first and last selfies.
- **Inside Mars:** click the crust, mantle and core.
- **Compare the twins:** Phoenix and InSight side by side.
- **Hear a marsquake:** the biggest quake InSight recorded, turned into sound.

It works on phones too: a full screen button, a landscape layout, and "Add to Home Screen" support on iPhone.

## Accuracy

- Every picture is labelled **REAL PHOTO**, **ILLUSTRATION** or **REAL DATA**, with its NASA ID.
- Drawn diagrams (orbits, layers of Mars, size comparisons) are marked *"Illustration, not to scale"*.
- Facts come from NASA's mission pages for [Mars Phoenix](https://science.nasa.gov/mission/mars-phoenix/) and [InSight](https://science.nasa.gov/mission/insight/), and from the captions of the images we use.

## NASA data and media used

**Images** (all from [images.nasa.gov](https://images.nasa.gov) / NASA Photojournal):
- **Phoenix:**
  - PIA11719 (self-portrait)
  - PIA10718 (work area, illustration)
  - KSC-07pd2174 and KSC-07pd2181 (launch)
  - PIA10705 (descending on its parachute, photographed by MRO)
  - PIA09701 (solar arrays test)
  - PIA10952 (robotic arm and the rock "Alice")
  - PIA09207 (robotic arm)
  - PIA10763 ("Dodo" trench)
  - PIA11059 ("Stone Soup" trench)
  - PIA10793 (panorama)
  - PIA11725 (one of its last images)
  - PIA22223 (landing site in 2008 and 2017)
- **InSight:**
  - PIA22228 and PIA22227 (illustrations)
  - PIA19402 and PIA19403 (assembly)
  - NHQ201805040004 (prelaunch)
  - VAFB-20180505-PH_CSH01_0001 (liftoff)
  - PIA22812 (landing, illustration)
  - PIA25282 (inner layers infographic)
  - PIA22977 (seismometer placed)
  - PIA23046 (heat probe)
  - PIA22959 (wind and thermal shield)
  - PIA24761 (seismogram)
  - PIA25827 (quakes through the core, illustration)
  - PIA25286 (dusty solar panel)
  - PIA22876 and PIA25287 (first and final selfies)

**Video and sound:**
- **PIA25281:** seismogram and sonification of InSight's biggest marsquake (May 4, 2022).
- **"Sounds of Mars: NASA's InSight Senses Martian Wind"** (NASA/JPL-Caltech/CNES/IPGP/Imperial College/Cornell). This is the real wind recorded by InSight's air pressure sensor on Dec 1, 2018, sped up 100× by NASA. We only filtered out bass that small speakers can't play.

Credits for each image are shown on screen and in the **Sources** panel on the website.

## Team

- Elvan Tuna Bülbül (captain)
- Umut Salih Eren
- Asya Akbulut
- Selman Akdoğan
- Isa Nesim Bozkus

The story, script, research, Allinol character and intro animation are the team's own work.

## Use of AI

- **Narration:** the voice was generated with ElevenLabs from the team's script.
- **Code and docs:** parts of the code, the animation timing, the sound effects and this README were made with help from Claude (Anthropic), an AI assistant.

## How it works

- **One page:** plain HTML, CSS and JavaScript, with no framework and no build step.
- **One renderer:** the whole documentary is drawn on a single canvas. Every frame is a function of time, so the same code plays it live on the website and exports the video.
- **Sound effects** are synthesized in the browser with the Web Audio API, so they need no outside sound files. They automatically turn down while someone is speaking.
- **Video export:** the 1920×1080, 60 fps MP4 is encoded in the browser with WebCodecs (H.264 + AAC) and [mp4-muxer](https://github.com/Vanilagy/mp4-muxer).

To run it on your own computer:

```bash
python3 tools/server.py 8765
```

Then open `http://localhost:8765`. The **Export MP4** button only appears there, not on the website.

## Files

| Path | What it is |
|---|---|
| `index.html` | The whole interactive documentary |
| `manifest.webmanifest` | Lets phones add it to the home screen |
| `assets/img` | NASA images |
| `assets/video` | Our intro and NASA's marsquake video |
| `assets/voice` | The narration, one file per line |
| `assets/audio` | InSight's Mars wind recording |
| `assets/icons` | App icons made from the Allinol character |
| `assets/vendor` | The mp4-muxer library |
| `tools/server.py` | Local server, used for exporting the video |
