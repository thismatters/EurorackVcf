# Voltage Controlled Filter

The Voltage Controlled Filter (VCF) filters incoming audio signals to the degree specified by the control voltages. This implementation uses a transistor ladder similar to that found in Moog synthesizers with both a cutoff frequency and a resonator control.

The circuit here is based on the [MiniMoog VCF](https://yusynth.net/Modular/EN/MOOGVCF/index.html) with minor tweaks to make it more Eurorack friendly. The changes I've made are thus:
* Selected resistors appropriate for +/-12V rails,
* Added polarity protection so that a backward power header doesn't fry anything (twin series schotty diodes: BAT54SL),
* Selected a modern dual NPN diode package for matched transistors,
* Full surface mount design.

The Yusynth page is a treasure trove of information about this circuit that I am too amateur to claim as my own; please read that outstanding page before using this circuit. The page provides many details and other implementations of this circuit that you may find suitable.

The KiCAD project here uses the library/footprints [found in my companion repo](https://github.com/thismatters/EurorackKiCAD).

## Width

8hp on a standard 3U rack.

## Inputs

Potentiometer labeled `cutoff` controls the cutoff frequency, which is also augmented by the `cv1` input and potentiometer. Two other CV inputs `cv2` and `cv3` combine with `cv1` and the `cutoff` knob to set the frequency. An additional potentiometer for setting the `emph`asis. Two audio signal inputs, `in1` and `in2` are adjusted for level by twin potentiometers and combine as the audio input to the filter.

## Output

A single output labeled `out` yields the filtered audio signal.

## Adjustment

### Volt per Octave tracking

1. Set the `cutoff` knob to its minimum setting (counterclockwise).
1. Set the `emph` knob to its minimum setting (counterclockwise).
1. Apply 0V to `cv2`.
1. Measure 0mV at the test point `TP1`.
1. Apply 1V to `cv2`.
1. Adjust RV6 to measure 18.2mV at `TP1`.
1. Apply 5V to `cv2`.
1. Adjust RV6 to measure 91mV at `TP1`.
1. Set the `emph` knob to its maximum setting (auto oscillation).
1. Connect a keyboard to `cv2` and play a scale.
1. Adjust RV6 to achieve good chromatic tracking.

### Frequency Range

1. Apply a 32Hz sine wave to `in1`.
1. Set the `emph` knob to its minimum setting.
1. Set the `cutoff` knob to its minimum setting.
1. Adjust RV7 until the 32Hz tone is muted.

### Emphasis

1. Adjust RV8 in order to reach auto-oscillation near 95% of the full range of the `emph` potentiometer.


## Vendors

There are part numbers in the [BOM](moog-vcf.csv) for many of the parts (not for basic passives though) at the following vendors:

* [Mouser](https://www.mouser.com): Needs no introduction. Get your ICs from here (or [digikey](https://www.digikey.com)).
* [Tayda Electronics](https://www.taydaelectronics.com/): Good supplier for passive components; audio jacks, and potentiometers. Their audio jacks are slightly smaller than the thonkiconn from thonk.
* [Love My Switches](https://lovemyswitches.com/): Has [really good knobs](https://lovemyswitches.com/anodized-aluminum-knob-the-lo-fi-1-4-smooth-shaft-12-5mm-od/) to go on those potentiometers!
* [OSHPark](https://oshpark.com/): Fast and (relatively) cheap PCB manufacturer. I haven't done a prototype run yet... stay tuned.

