# My Tutorial

## Step 1 - Make two variables
Today we are going to explore how WHILE loops work. To do this, we will create a compass that leads the user to a secret hidden treasure.

First, create a variable called heading.

Go to the ``||variables:Variables||`` category and click on ``Make a variable...`` and make a variable called heading.
```blocks
```

## Step 2

Set the heading to 0.

Go to the ``||input:Input||`` category, click **more** and snap the ``||input:calibrate compass||`` block into the ``||basic:on start||`` block.

```blocks
input.calibrateCompass()
let heading = randint(1, 360)
```

Congratulations, you did it! :)
