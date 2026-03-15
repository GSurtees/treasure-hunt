# Treasure Hunt

## Step 1 - Create your variables
We are going to create a compass that leads you to hidden treasure!

First, create two variables. Go to ``||variables:Variables||`` and click ``Make a variable...`` to create one called **heading** and another called **found**.

## Step 2 - Set up the compass
Go to ``||input:Input||``, click **More** and add a ``||input:calibrate compass||`` block inside ``||basic:on start||``.
```blocks
let heading = 0
let found = false
input.calibrateCompass()
```

## Step 3 - Pick a random heading
Go to ``||variables:Variables||`` and add a ``||variables:set heading to||`` block. Then go to ``||math:Math||`` and place a ``||math:pick random||`` block inside it, set to **0** and **360**.
```blocks
input.calibrateCompass()
let heading = randint(0, 360)
```

## Step 4 - Show the starting icons
Go to ``||basic:Basic||`` and add a ``||basic:show icon||`` block set to the **Confused** face. Then add two ``||basic:show leds||`` blocks to draw an H and an arrow. Add a ``||basic:pause||`` of 200ms between them. Finish with a ``||basic:clear screen||``.
```blocks
input.calibrateCompass()
let heading = randint(0, 360)
basic.showIcon(IconNames.Confused)
basic.showLeds(`
    . . # . .
    . # . # .
    . # # # .
    . # . # .
    . # . # .
    `)
basic.pause(200)
basic.showLeds(`
    . . # . .
    . # . . .
    # # # # #
    . # . . .
    . . # . .
    `)
basic.clearScreen()
```

## Step 5 - Add the button handler
Go to ``||input:Input||`` and drag an ``||input:on button A pressed||`` block onto the canvas.
```blocks
input.onButtonPressed(Button.A, function () {
})
```

## Step 6 - Add the while loop
Go to ``||loops:Loops||`` and add a ``||loops:while||`` block inside the button handler. Go to ``||logic:Logic||`` and use a **not** block, then go to ``||variables:Variables||`` and place **found** inside it.
```blocks
input.onButtonPressed(Button.A, function () {
    while (!(found)) {
    }
})
```

## Step 7 - Show the searching icon
Inside the while loop, go to ``||basic:Basic||`` and add a ``||basic:show icon||`` block set to the **Confused** face.
```blocks
input.onButtonPressed(Button.A, function () {
    while (!(found)) {
        basic.showIcon(IconNames.Confused)
    }
})
```

## Step 8 - Check the compass heading
Go to ``||logic:Logic||`` and add an ``||logic:if then||`` block. For the condition, go to ``||logic:Logic||`` and use a **less than or equal** block. On the left side, go to ``||math:Math||`` and use **absolute of**, then go to ``||input:Input||`` and place ``||input:compass heading||`` inside it. Subtract **heading** from it. Set the right side to **10**.
```blocks
input.onButtonPressed(Button.A, function () {
    while (!(found)) {
        basic.showIcon(IconNames.Confused)
        if (Math.abs(input.compassHeading() - heading) <= 10) {
        }
    }
})
```

## Step 9 - Found the treasure!
Inside the if block, go to ``||variables:Variables||`` and set **found** to **true**. Then add a ``||basic:show icon||`` set to **Happy**. Go to ``||music:Music||`` and add **play melody entertainer until done**. Then add **stop all sounds** and ``||basic:clear screen||``.
```blocks
input.onButtonPressed(Button.A, function () {
    while (!(found)) {
        basic.showIcon(IconNames.Confused)
        if (Math.abs(input.compassHeading() - heading) <= 10) {
            found = true
            basic.showIcon(IconNames.Happy)
            music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Entertainer), music.PlaybackMode.UntilDone)
            music.stopAllSounds()
            basic.clearScreen()
        }
    }
})
```

## Step 10 - Test it!
Press **Button A** and point your micro:bit in different directions. When the compass heading matches the secret heading, you've found the treasure! 🎉
