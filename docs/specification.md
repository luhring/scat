# Scat Language Specification

## Introduction

Scat is a text-based notation language designed to simplify the entry of musical sequences, chords, and arpeggios. It's optimized for use in terminal environments and can be easily translated into MIDI data, making it suitable for incorporation into various music creation workflows.

_"Scat"_ is an acronym for "Sequences, Chords, (and) Arpeggios (as) Text".

## Syntax

### Step

A step is a [single note](#single-note), a [chord](#chords), or a [rest](#rests). It is the atomic unit of a [stream](#stream).

E.g. `C`, `$Dm`, or `-`

### Stream

A stream is a space-delimited list of one or more [steps](#step).

E.g. `C D E G`, `$Dm7 $G7`, `F`, or `C - E - G - E -`

### Single note

A single note is expressed by its [note letter](#note-letters), an [accidental](#accidentals) (flat or sharp) if applicable, and an [octave](#specifying-an-octave).

#### Note Letters

A note letter is one of the following: `A`, `B`, `C`, `D`, `E`, `F`, or `G`.

#### Accidentals

Flat notes are expressed as a note letter followed by a `b`, and sharp notes are expressed as a note letter followed by a `#`. There is no natural sign: notes expressed without an accidental are always interpreted as natural notes.

E.g. `Bb` for B-flat, `F#` for F-sharp, or `C` for C-natural

#### Specifying an octave

A single note's octave may be specified in one of two ways: as an [absolute octave](#absolute-octave) or as a [relative octave](#relative-octave).

##### Absolute Octave

An absolute octave is specified as a single-digit integer (from `0` to `9`, inclusive) following the [note letter](#note-letters) and its [accidental](#accidentals) if present.

E.g. `C4 Eb5 C6`

##### Relative Octave

Alternatively, a note's octave may be specified by a preceding plus (`+`) or minus (`-`) sign to indicate a _relative_ octave (that is, relative to the most recently used octave).

E.g. `C4 +E -C -G`, equivalent to `C4 E5 C4 G3`

It is illegal to specify both an absolute and a relative octave for a single note.

##### Default Octave

Specifying a note's octave is not required. At the beginning of a stream, the octave is assumed to be `4` until otherwise specified. This means that the following two streams are equivalent:

- `C4 D4 E4 F4 G4 A4 B4 C5`
- `C D E F G A B +C`

As soon as an octave is specified, it remains in effect until a new octave is specified (either absolutely or relatively) or the stream ends.

##### Octave Boundary

As is standard in Western music notation, the available series of ascending notes changes octave at each _C_ note. (For example, here's a continuous sequence of neighboring notes: `B3 C4 D4 E4 F4 G4 A4 B4 C5`.)

### Rests

A rest is a _silent_ step — it does not produce any sound. It may be used in place of a [single note](#single-note) or [chord](#chords).

A rest is expressed as a hyphen (`-`).

### Chords

A chord is expressed as either a [chord literal](#chord-literals) or as a [named chord](#named-chords).

#### Chord Literals

A chord literal is an explicit, space-delimited set of single notes surrounded by square brackets (`[` and `]`).

E.g. `[C E G]`

The following rules apply to the list of single notes of a chord literal:

1. The notes must be in ascending order.
2. Notes may not be duplicated.

#### Named Chords

A named chord is a pre-defined chord referenced by "name" instead of spelled out literally. A named chord is denoted with a dollar sign (`$`) prefix.

The syntax for a named chord is: `$<note><quality><octave>`. The `<quality>` and `<octave>` components are optional.

##### Qualities for Named Chords

Here are the available named chord qualities (and their specifiers):

- major (no specifier used) — e.g. `$C`, same as `[C E G]`
- minor (`m`) — e.g. `$Am`, same as `[A +C E]`
- dominant seventh (`7`) — e.g. `$G7`, same as `[G B +D F]`
- major seventh (`M7`) — e.g. `$CM7`, same as `[C E G B]`
- minor seventh (`m7`) — e.g. `$Dm7`, same as `[D F A +C]`
- diminished (`dim`) — e.g. `$Bdim`, same as `[B +D F]`
- augmented (`aug`) — e.g. `$Eaug`, same as `[E G# +C]`
- half-diminished seventh (`m7b5`) — e.g. `$Fm7b5`, same as `[F Ab +Cb Eb]`
- fully-diminished seventh (`dim7`) — e.g. `$Gdim7`, same as `[G Bb +Db Fb]`
- suspended fourth (`sus4`) — e.g. `$Gsus4`, same as `[G +C D]`
- suspended second (`sus2`) — e.g. `$Dsus2`, same as `[D E A]`

##### Octaves for Named Chords

With named chords, octaves are specified with an "at sign" (`@`) prefix — e.g. `@4`, instead of just the `4` used with single notes — to disambiguate chord octaves from [chord qualities](#qualities-for-named-chords) that are named only by a number (e.g. a `$C7` chord). The chord octave specifies the octave of the _root note_ of the chord.

E.g. `$G7@2`, equivalent to `[G2 B2 D3 F3]`

[Relative octaves](#relative-octave) **cannot** be used to specify the octave of a named chord.

#### Chord Articulations and Arpeggiation

TODO!

## Examples

TODO!

## Contribution Guidelines

For guidelines on how to contribute to the Scat specification, please see [CONTRIBUTING.md](CONTRIBUTING.md).

## License

This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).
