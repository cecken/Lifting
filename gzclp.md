# Week 1
## Day 1
/// The GZCLP logic is pretty tricky, so the code below may look intimidating.
/// If you want to figure it out how it works, watch this video:
/// https://www.youtube.com/watch?v=1sOr8pS9tl4
///
/// But if you just want to tweak the program slightly and add/change some T3s,
/// simply add them at the end of each day, reusing t3: Lat Pulldown.
/// As an example, there're some optional T3s commented out below (i.e. prefixed with ///).
/// Remove triple slashes (///) there if you want to add them to the program.








// **T1**. It starts with **85% of 5RM** (or approximately **75% or 1RM**).
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it
// Rounding should be 2x the smallest plate you have access to.

// ! **T1**.

// **T1**. Retest week, you may skip warmups. Find your new 5RM (5 rep max), as follows
// * Start with the bar, do 5 reps.
// * Throw on some more weight, do 5 reps.
// * Repeat, when the bar starts to get heavy, make smaller jumps.
// * When you finally get to a set that is hard, but you do it - take that number, long press **5RM Test** set, and set the weight you did
// * Tap on the "New 5RM" set to mark it completed
t1: Squat / 4x3, 1x3+ / 5x2, 1x2+ / 9x1, 1x1+ / 1x5 (5RM Test) / 185lb / 180s / progress: custom(increase: 10lb) {~
  if (descriptionIndex == 1) {
    descriptionIndex = 2
  }
  if (setVariationIndex == 4) {
    descriptionIndex = 2
    setVariationIndex = 1
    weights = weights[1] * 0.85
    rm1 = weights[1] / rpeMultiplier(5, 10)
  } else if (completedReps >= reps) {
    if (completedReps[ns] > 9){
      weights = weights[ns] + (2* state.increase)
    } else {
    weights = weights[ns] + state.increase
      }
  } else if (setVariationIndex == 3) {
    descriptionIndex = 3
    setVariationIndex += 1
  } else {
    setVariationIndex += 1
  }
~}




// **T2**. Start with **65% of 5RM**.
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it
// Rounding should be set to 2x the lowest plate you have access to

// ! **T2**.
t2: Bench Press / 3x10 / 3x8 / 3x6 / 97.5lb / 120s / progress: custom(stage1weight: 0lb, increase: 2.5lb, stage3increase: 10lb) {~
  if (descriptionIndex == 1) {
    descriptionIndex = 2
  }
  if (completedReps >= reps) {
    weights = weights[ns] + state.increase
  } else if (setVariationIndex == 1) {
    state.stage1weight = weights[ns]
    setVariationIndex += 1
  } else if (setVariationIndex == 2) {
    setVariationIndex += 1
  } else {
    setVariationIndex = 1
    weights = state.stage1weight + state.stage3increase
  }
~}

// **T3**.
// Weight progression here needs to be individualized to the workout equipment
// Leverage machines are dependent on the machines weight settings.
// Cable excercises follow an odd progression based on modulus due to uneven increments
t3: Lat Pulldown, Leverage Machine / 2x15, 1x15+ / 85lb / 60s / progress: custom() {~
  if (completedReps[ns] >= 25) {
    weights = weights[ns] + 5lb
  }
~}
t3: Cable Crunch / 2x15, 1x15+ / 10.5lb / 60s / progress: custom(step: 2) {~
    if (completedReps[ns] >= 25) {
        state.step += 1
        if ((state.step % 3) == 0){
          weights += 2
        }
        else {
          weights += 1.5
        }
      }
~}
t3: Leg Extension, Leverage Machine / 2x15, 1x15+ / 30lb / 60s / progress: custom() { ...t3: Lat Pulldown, Leverage Machine}

## Day 2
// **T1**. It starts with **85% of 5RM** (or approximately **75% or 1RM**).
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it

// ! **T1**.

// **T1**. Retest week, you may skip warmups. Find your new 5RM (5 rep max), as follows
// * Start with the bar, do 5 reps.
// * Throw on some more weight, do 5 reps.
// * Repeat, when the bar starts to get heavy, make smaller jumps.
// * When you finally get to a set that is hard, but you do it - take that number, long press **5RM Test** set, and set the weight you did
// * Tap on the "New 5RM" set to mark it completed
t1: Overhead Press / 4x3, 1x3+ / 5x2, 1x2+ / 9x1, 1x1+ / 1x5 (5RM Test) / 100lb / progress: custom(increase: 5lb) { ...t1: Squat }




// **T2**. Start with **65% of 5RM**.
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it

// ! **T2**.
t2: Deadlift / 3x10 / 3x8 / 3x6 / 140lb / progress: custom(stage1weight: 0lb, increase: 5lb, stage3increase: 10lb) { ...t2: Bench Press }

// ...t3: Lat Pulldown[1]
t3: Seated Row, Leverage Machine / ...t3: Lat Pulldown, Leverage Machine[1] / 55lb / progress: custom() { ...t3: Lat Pulldown, Leverage Machine }
t3: Lateral Raise, Cable / ...t3: Lat Pulldown, Leverage Machine[1] / 4lb / progress: custom(step: 0) { ...t3: Cable Crunch }
t3: Preacher Curl, EZ Bar / ...t3: Lat Pulldown, Leverage Machine[1]

## Day 3
// **T1**. It starts with **85% of 5RM** (or approximately **75% or 1RM**).
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it

// ! **T1**.

// **T1**. Retest week, you may skip warmups. Find your new 5RM (5 rep max), as follows
// * Start with the bar, do 5 reps.
// * Throw on some more weight, do 5 reps.
// * Repeat, when the bar starts to get heavy, make smaller jumps.
// * When you finally get to a set that is hard, but you do it - take that number, long press **5RM Test** set, and set the weight you did
// * Tap on the "New 5RM" set to mark it completed
t1: Bench Press / 4x3, 1x3+ / 5x2, 1x2+ / 9x1, 1x1+ / 1x5 (5RM Test) / 140lb / progress: custom(increase: 5lb) { ...t1: Squat }




// **T2**. Start with **65% of 5RM**.
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it

// ! **T2**.
t2: Squat / 3x10 / 3x8 / 3x6 / 130lb / progress: custom(stage1weight: 0lb, increase: 5lb, stage3increase: 10lb) { ...t2: Bench Press }

// ...t3: Lat Pulldown[1]
t3: Lat Pulldown, Leverage Machine / ...t3: Lat Pulldown, Leverage Machine[1]
t3: Cable Crunch / ...t3: Cable Crunch[1]
t3: Leg Extension, Leverage Machine / ...t3: Leg Extension, Leverage Machine[1]

## Day 4
// **T1**. It starts with **85% of 5RM** (or approximately **75% or 1RM**).
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it

// ! **T1**.

// **T1**. Retest week, you may skip warmups. Find your new 5RM (5 rep max), as follows
// * Start with the bar, do 5 reps.
// * Throw on some more weight, do 5 reps.
// * Repeat, when the bar starts to get heavy, make smaller jumps.
// * When you finally get to a set that is hard, but you do it - take that number, long press **5RM Test** set, and set the weight you did
// * Tap on the "New 5RM" set to mark it completed
t1: Deadlift / 4x3, 1x3+ / 5x2, 1x2+ / 9x1, 1x1+ / 1x5 (5RM Test) / 215lb / progress: custom(increase: 10lb) { ...t1: Squat }




// **T2**. Start with **65% of 5RM**.
// You can adjust your 1RM by clicking the **edit** icon, and setting the **1 Rep Max** value.
// There's the RM calculator there to help find it out if you don't know it

// ! **T2**.
t2: Overhead Press / 3x10 / ! 3x8 / 3x6 / 70lb / progress: custom(stage1weight: 62.5lb, increase: 5lb, stage3increase: 5lb) { ...t2: Bench Press }

// ...t3: Lat Pulldown[1]
t3: Seated Row, Leverage Machine / ...t3: Lat Pulldown, Leverage Machine[1] / 55lb
t3: Lateral Raise, Cable / ...t3: Cable Crunch[1] / 4lb
t3: Preacher Curl, EZ Bar / ...t3: Lat Pulldown, Leverage Machine[1]
