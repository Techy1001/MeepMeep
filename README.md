# MeepMeep
[![Release](https://jitpack.io/v/NoahBres/MeepMeep.svg)](https://jitpack.io/#NoahBres/MeepMeep)

Path creation/visualization tool for Road Runner

# 🔨 Installing 

## Gradle Snippet:
```groovy
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    implementation 'com.github.NoahBres:MeepMeep:1.0.0'
}
```

## Installation Video

[![YouTube Installation Video](/images/readme/thumbnail-half.jpg?raw=true)](https://youtu.be/vdn1v404go8)

## Run Sample
```java
package com.example.meepmeeptesting;

import com.acmerobotics.roadrunner.geometry.Pose2d;
import com.noahbres.meepmeep.MeepMeep;
import com.noahbres.meepmeep.core.colorscheme.scheme.ColorSchemeRedDark;

public class MeepMeepTesting {
    public static void main(String[] args) {
        // Declare a MeepMeep instance
        // With a field size of 800 pixels
        MeepMeep mm = new MeepMeep(800)
                // Set field image
                .setBackground(MeepMeep.Background.FIELD_ULTIMATE_GOAL_DARK)
                // Set theme
                .setTheme(new ColorSchemeRedDark())
                // Background opacity from 0-1
                .setBackgroundAlpha(1f)
                // Set constraints: maxVel, maxAccel, maxAngVel, maxAngAccel, track width
                .setConstraints(60, 60, Math.toRadians(180), Math.toRadians(180), 15)
                .followTrajectorySequence(drive ->
                        drive.trajectorySequenceBuilder(new Pose2d(0, 0, 0))
                                .forward(30)
                                .turn(Math.toRadians(90))
                                .forward(30)
                                .turn(Math.toRadians(90))
                                .forward(30)
                                .turn(Math.toRadians(90))
                                .forward(30)
                                .turn(Math.toRadians(90))
                                .build()
                )
                .start();
    }
}
```