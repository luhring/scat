# Scat

An ASCII notation for musical sequences, chords, and arpeggiations

[![CC BY 4.0][cc-by-shield]][cc-by]

Scat is a text-based notation designed to simplify the entry of musical sequences, chords, and arpeggiations. It is optimized for use in terminal environments and can be easily translated into MIDI data, making it suitable for incorporation into various music creation workflows.

_"Scat"_ is an acronym for "**Sequences**, **Chords**, (and) **Arpeggios** (as) **Text**".

## Features
- **Simple and Readable**: Designed for easy reading and writing of musical notation.
- **Terminal-Friendly**: Ideal for composing music directly from the terminal.
- **MIDI-Compatible**: Easily translatable into MIDI format for further musical production.
- **Flexible**: Supports sequences, chords, and various arpeggiation patterns.

## Specification

The full specification of the Scat language can be found in the [specification document](docs/specification.md). Feedback and contributions are welcome!

## What does it look like?

Scat notation is stored and transmitted as a [stream](./docs/specification.md#stream) — a space-delimited list of [steps](./docs/specification.md#step). Each step can be a [note](./docs/specification.md#single-note), a [chord](./docs/specification.md#chords), or a [rest](./docs/specification.md#rests).

Here are some examples of Scat streams:

1. Simple sequence of notes:

       C D E F G F E D C

2. Chord progression:

       $C $Am $F $G

## Contributing
We welcome contributions! Please see [CONTRIBUTING.md](contributing.md) for guidelines on how to contribute to the project.

## License
This work is licensed under a [Creative Commons Attribution 4.0 International License][cc-by].

[cc-by]: https://creativecommons.org/licenses/by/4.0/
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
