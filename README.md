# atc_parser

## Description

An example of an air traffic control utterance intent classifier based on a linear source vector machine algorithm.  In its current state it does little more than utilize single-word n-grams, each converted into its own feature vector, then given a binary weight of 1 (word present in sentence) or 0 (not present).  This is then trained upon, and a new test utterance classified with the resulting model.

Note that the training data is exceptionally sparse and many more feature vectors incorporating 2+ n-grams, syntactic relationship, etc. should be added to make this more than a simplistic demo.

## Current Training Data (In Full)

Each row consists of an `utterance` and an `intent classification label`:

```
ground ready to taxi,"ready to taxi"
taxi via to runway,"taxi to runway"
tower holding short ready to takeoff,"holding short runway"
takeoff runway,"takeoff confirmed"
tower midfield downwind for runway,"pattern location"
taxi via to ramp,"taxi to ramp"
```

## Current Feature Vector Map

The training data above results in the following feature vector mappings:

```
{
  "ground": 0,
  "ready": 1,
  "to": 2,
  "taxi": 3,
  "via": 4,
  "runway": 5,
  "tower": 6,
  "holding": 7,
  "short": 8,
  "takeoff": 9,
  "midfield": 10,
  "downwind": 11,
  "for": 12,
  "ramp": 13
}
```

## Example Output of Model

```
Input utterance:
	approaching right midfield downwind
Input utterance as feature vectors and weights:
	[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0]
That was classified as:
	pattern location
```