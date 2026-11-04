Line-following robot: power system schematic (KiCad)
Schematic for my mechatronics line-follower: an Arduino Uno, an L298N driving two DC motors, three IR line sensors plus an IR receiver, two servos, and two 7.2V packs in series (14.4V) with a 5A fuse per pack and a main switch.

The part I’m happiest with is the power fix. My first version tapped the midpoint between the two batteries and fed it into the Arduino’s Vin, so the Uno’s onboard regulator made the 5V for the logic. With noisy motors on the same supply, the logic kept misbehaving, and the onboard regulator wasn’t up to it. I rebuilt it so the full 14.4V goes to a dedicated 5V regulator (U2), whose output goes straight into the Arduino’s 5V pin and onto the sensor and servo rail, with the L298N motor supply taking raw battery voltage. That separated the logic supply from the motor noise. [Add one line on how you knew it worked, e.g. “after that the logic stopped glitching.”]

What I’d change: I don’t see decoupling or bulk capacitors on the regulator or the motor supply in this schematic, and dropping 14.4V to 5V with a linear regulator wastes power as heat, so next time I’d add caps and use a buck converter.
