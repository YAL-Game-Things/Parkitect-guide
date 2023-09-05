Time to time the game will bestow a random event upon you. Some are good, some are less good. Events are chosen based on their weight, so 2x the weight makes the event 2x more likely to be chosen instead of other events.

## Supply surplus
Makes one of the shop resources 10..50% cheaper for a time.

Event weight of 1.5

## Supply shortage
Makes one of the shop resources 10..50% more expensive for a time.

Event weight of 1.5

## Ride part shortage
While active, ride repairs are ~3 times less effective at restoring safety.

Event weight is set to (1 / (average safety))², and thus:

| Average ride safety | Event weight |
| ------------------- | ------------ |
| 100%                | 1            |
| 70%                 | ~2           |
| 50%                 | 4            |

## Increase in visitors
Increases max guest count by 1/9 .. 1/3 for a time.

Event weight of 1.25

## Decrease in visitors
Decreases max guest count by 1/9 .. 1/3 for a time.

Event weight of 1.25

## Vandalism
A handful of guests (8..15) turn into vandals.

Vandals act mostly like normal guests, but will periodically break your path attachments (benches, lamps, trash bins), which makes them happy and makes the rest of the guests passing by the tile not so happy. An engineer will repair path attachments that they walk by, but you can also drop them yourself next to broken things (use "vandalism" overlay).

Security guards will catch and ban vandals when they see them, but you can also do so yourself - you can tell them apart by them wearing black backwards baseball caps, bandanas, and by the "Vandal" trait in the last tab. The "Ban" button is in the first tab.

The event weight formula goes like this (in `VandalismWaveEvent`)

> guest ratio = (guest count) / ((guard count) * 220)  
> rating ratio = 1 - (park overall rating) * 0.1  
> event weight = min(2, (rating ratio) * ((guest ratio) ^ 1.3))

So, assuming Park Overall Rating of 90%,

| Guard : guest ratio | Event weight |
| --- | --- |
| 1 : 400 | 2 |
| 1 : 240 | 1 |
| 1 : 140 | 1/2 |
| 1 : 82  | 1/4 |
| 1 : 48  | 1/8 |


## "A bus dropped off X guests who prefer Y intensity rides"
Guest count can be anything between (park guest count) / 10 and (park guest count) / 4, but no less than 20 and no more than 50.

Event weight of 0.75.

## "A bus dropped off X <attraction> fans"
Picks a random open & reachable ride, but apparently only rides with intensity under 100.

Same guest count rules as above.

Event weight of 0.75.

## "The ride will have an increase in customers for a time"
Makes guests more likely to pick the given ride, which doesn't mean too much.

Event weight of 1.5.
