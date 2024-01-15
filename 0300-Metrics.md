## Experiences rating
Each guest's Experiences Rating is calculated as

> (number of positive opinions) / ((number of positive opinions) + (number of negative opinions))

You can see a list of these on the Thoughts tab when clicking on a guest, or Opinions tab in Park Info. Neutral opinions (marked with a 😐) don't count as either positive or negative.

## Maximum guest count
If you are playing through the campaign or just trying to build a Big Park, you might be wondering what does the guest count depend on, and how do you get more guests in your park.

**Short version:** build more rides, preferably different and/or exciting ones.

**Long version:**
Each ride attracts
> (ride's excitement rating) * 0.8 * (0.8 + 0.2 * (ride's satisfaction rate))

guests, so a ride with 50 excitement and 100% satisfaction will yield you extra 40 guests or so.
Having more than 3 of the same ride will apply a slight penalty to their bonus (-10% at 4, -19% at 5, -25% at 6, -30% at 7, -33% at 8 or more).

Each shop attracts up to 5 extra guests, depending on its satisfaction rating.

Park's overall rating is used *roughly* as a multiplier (~half the guests at 50% rating), but can't drop below 15%.

*Technical:* `Park.calculateMaxGuestCount`

## Park entrance fee
Generally it's good to leave park entrance fee at default value of $1 and rely on ride fees,
but the scenarios will occasionally ask you to build a park where the rides are free.

In such case you can set the park entrance fee to roughly 2x of sum of all rides' would-be admission fees.

*Technical:* `Park.calculateValueFor`