# Badminton Corner Randomizer

A small browser app for random badminton shadow footwork and corner drills. It gives you realistic movement cues with shot-dependent timing, so the session feels closer to rally footwork than fixed-interval shadowing.

You can find the hosted version here: https://buschjaeger.it/badminton_corner_randomizer/

## Features

- 6-corner movement cues for front, mid, and back court
- configurable fast / medium / slow shot timings
- optional shot label together with the corner cue
- configurable reps, sets, and countdowns
- active and passive breaks between sets
- works as a single local HTML file without a backend
- installable as an offline-capable web app when hosted over HTTP(S)
- large fullscreen display with audio cues for gym or hall use

## Shot distribution and timing

The app does not use fixed patterns. It generates the next corner randomly, but with a badminton-style bias:

- 50% front ↔ back transitions
- 30% same-zone transitions
- 20% transitions through mid court
- 6% chance to repeat the same corner directly

Timing is based on the transition between zones:

- fast: front → front or mid → mid exchanges
- medium: front/mid transitions
- slow: any transition involving the back court

Each cue cycle has three parts:

1. move to the shown corner
2. recover
3. a fixed 250 ms split-step phase before the next cue

The 250 ms split-step window is close to reported elite split-step reaction times of about 0.25 s. Reported rally timing in badminton is also very short: one cited review notes the shuttle is often returned about 0.93 s after a shot, and Rio 2016 men’s singles average rally duration was about 9.5-10.2 s for roughly 8.0-8.9 strokes, which is about 0.9 shots per second on average. The app uses that as inspiration, but maps it to a simple training model with three configurable buckets instead of trying to reproduce full match statistics exactly.

Personally, I find pro timing a bit too fast for footwork-only work at home, so a practical starting point is:

- fast: 0.9 s
- medium: 1.2 s
- slow: 1.4 s

The app then samples around those anchors rather than repeating the exact same delay every time. I do not have space for full-court movements at home, but I usually do 1.5-2 steps (i.e. split step -> directional step -> 1 additional step). 

## References

1. Torres-Luque et al., Statistical Differences in Set Analysis in Badminton at the RIO 2016 Olympic Games. https://pmc.ncbi.nlm.nih.gov/articles/PMC6457257/
2. Yüksel and Tunç, Examining the Reaction Times of International Level Badminton Players Under 15. https://pmc.ncbi.nlm.nih.gov/articles/PMC5969201/
3. Guo et al., Biomechanical Effects of the Badminton Split-Step on Forecourt Lunging Footwork. https://pmc.ncbi.nlm.nih.gov/articles/PMC11117488/
4. Shishido and Nishijima, Characteristics of split-step skills of the world’s top athletes in badminton. https://pmc.ncbi.nlm.nih.gov/articles/PMC11698525/
