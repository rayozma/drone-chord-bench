# Drone Chord Bench

A browser simulator for making music with the hover sound of multirotor drones: tune three quadcopters to a chord, play chord progressions with collective-pitch drones, and play melodies on a tethered fixed-pitch drone. It predicts the sound level and spectrum at a microphone, outdoors or indoors, and synthesizes the sound live.

Open `index.html` in a browser, or view it on GitHub Pages.

## Background

- **Where the hum comes from:** propeller noise dominates. Its pitch is the blade passing frequency (BPF), `f = blades × RPM / 60`, plus integer harmonics. Brushless motors and ESCs add a smaller whine.
- **Why a hovering drone has one note:** with fixed-pitch props, thrust must equal weight, so hover RPM (and pitch) is fixed by weight, prop geometry and air density.
- **Ways to change pitch:**
  - Payload or prop choice (offline tuning).
  - Collective-pitch rotors: a governor sets RPM while blade pitch holds thrust.
  - Tethering: thrust can exceed weight, so a drone can play from its hover note up to full throttle. The range in semitones above hover is `6 × log2(T/W)`.
- **Measuring:** use a Class 1 meter or calibrated measurement mic, a 94 dB calibrator and a windscreen. Record at least 30 s of steady hover with ≥10 dB margin over background. Report Leq in dB(A), plus a Welch PSD or spectrogram, and compare the peaks to the BPF computed from logged RPM.

## Simulator features

- **Scenarios:** outdoor (wind, grass or concrete ground, temperature, elevation) and indoor (room presets, absorption, Sabine RT60, critical distance).
- **Measurement controls:** distance, microphone height, hover height and drone spacing.
- **Realistic configuration:** airframe class, prop diameter, pitch, blade count and payload, with throttle, thrust-to-weight, tip Mach and power checks. Auto-tuning to a note or chord, in just or equal temperament.
- **Collective-pitch airframes:** governor head speed, collective readout, governor lag, and chord progressions with automatic voice leading.
- **Tethered mode:** tension readout, playable range, melody player with fit-to-range, and a live keyboard (mouse, or the A–K keys; Z and X shift the octave).
- **Acoustics:** spherical spreading, air absorption, ground-reflection interference, and a diffuse reverberant field. The spectrum is a 1/96-octave narrowband view, with dB(A) and dB(Z) totals.

## Model limits

Thrust coefficients and the 1 m noise levels are generic fits, not data for specific props. Treat absolute levels as ±5 dB estimates; relative changes are more reliable. Governor droop and altitude transients during note changes are not modelled.

## Next steps (hardware)

1. Characterize one drone on a thrust stand: RPM to measured pitch, pitch stability, thrust-to-weight.
2. Closed-loop RPM-to-note control using ESC RPM telemetry.
3. Tethered single-drone melody.
4. Scale up to several tethered or free-hovering drones for harmony.
