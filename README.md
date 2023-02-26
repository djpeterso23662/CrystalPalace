Crystal Palace
==============

This repository contains the Crystal Palace plugin for VCV Rack. If you like to
create weird soundscapes, drifting ambient music, or put your electronica in a
blender, you have come to the right place.

The Crystal Palace plugin is free, closed-source, and released under license.
VCV Rack is written by Andrew Belt; this plugin uses the VCV Rack API and is
offered in compliance with Andrew’s license. The Crystal Palace plugin for VCV
Rack was written by David Peterson.

Compiled releases of Crystal Palace are available from the Releases page and
from the VCV Rack Plugins page.

![Crystal Palace plugin](https://github.com/djpeterso23662/CrystalPalace/blob/master/res/CrystalPalace_Family.jpg)

What is a Crystal Palace?
-------------------------

The Crystal Palace for which this VCV plugin is named was invented by BBC
Radiophonic Workshop engineer Dave Young in 1967-8. The Crystal Palace consists
of sixteen input jacks connected so that the received signal is shared by the
higher-numbered jacks when they are unoccupied. For example, if inputs are
connected to jacks 1 and 9, unconnected channels 2 through 8 receive the jack 1
signal, and unconnected jacks 10 through 16 receive the jack 9 signal. The
sixteen input channels are connected to non-rotating input vanes arranged in a
circle within a multiplexer drum. A re-purposed variable-speed dictation machine
motor rotates a capacitance vane around the circle of input vanes without
touching them, forming a smooth capacitive fader. The capacitive vane is
connected to the high-impedance input of a field-effect transistor (FET)
amplifier using the gold nib of a Conway-Stewart fountain pen. The amplified
signal is connected to four output jacks. The device is housed in a hand-made
Perspex box, which gives it its name. The Crystal Palace was used by Brian
Hodgson on his soundtrack for “The Krotons” episodes of *Doctor Who* in 1968, as
well as “Music of the Brisbane School” for Philip Saville’s *The Machine Stops*.

Modules
-------

### Perspex

The Perspex module is inspired by Dave Young’s Crystal Palace for VCV Rack.
While it is essentially a sixteen-channel mixer, it can also be used to create a
custom sound source or a complex low frequency oscillator (LFO). Perspex extends
the original Crystal Palace device with clock, reset, and control voltage (CV)
inputs useful in the Eurorack environment.

Perspex accepts up to sixteen channels of inputs. The input signals are
cross-faded as Perspex’s motor rotates the capacitance vane past each of the
stationary input vanes. Each channel fades out as the next channel fades in,
with an equal-power cross-fade.

Perspex is a fairly large module and is not skiff-friendly. Perspex is 34 HP
wide and, due to the motor and multiplexer drum, is nearly 34 HP deep as well.

### IN 1 through IN 16

The Perspex module accepts up to sixteen inputs through the sixteen numbered
jacks on the left side of its panel. Each input jack is wired to the next,
higher-numbered input jack (normaled). For example, the signal on channel 1 will
also be present on channel 2 if jack 2 is not connected, as well as on channel 3
if both jack 2 and jack 3 are not connected, and so on around the circle. If
jack 1 is not connected channel 1 will contain silence and will pass the silent
signal to higher-numbered channels. The signal received through Jack 16 is not
connected to channel 1. Signals input or passed around the circle to channel 16
will not be passed to channel 1.

### CLOCK

A clock signal can be connected to the CLOCK input jack. When the CLOCK jack is
connected Perspex advances the capacitance vane by one revolution for each pulse
received. It is very likely that you will want to send every fourth or sixteenth
pulse to Perspex using a clock divider. When the CLOCK input jack is connected
Perspex ignores the CV jack and the SPEED knob.

A low frequency oscillator (LFO) can be connected to the CLOCK input jack. The
LFO signal causes Perspex to advance the capacitance vane by one revolution per
cycle of the LFO (sync mode).

### RESET

When Perspex receives a pulse on the RESET input jack, the position of the
capacitance vane is instantly moved to channel 1 (the top of the circle on the
panel). Channel 1 then fades as the capacitance vane moves past it. When a reset
occurs the rotation of the capacitance vane is disturbed, likely resulting in an
audible interruption of the output signal.

### CV

When Perspex receives a control voltage (CV) signal through the CV input jack,
the value is added to the speed set on the SPEED knob. When a positive signal is
received the speed of rotation is increased; when a negative signal is received,
the speed is decreased. A sufficiently low combination of CV input and the SPEED
knob will halt the motor. The motor will never spin backwards due to limitations
of its gearing. When the CLOCK input jack is connected, the CV input is ignored
(sync mode).

### SPEED

The SPEED knob controls the speed of Perspex’s motor. The left side of the SPEED
knob’s range is slower. The right side of the SPEED knob’s range is faster. The
value set on the SPEED knob is combined with the value received from the CV
input jack. When the CLOCK input jack is connected, the SPEED knob is ignored
(sync mode).

### NORMAL LED 1 through NORMAL LED 16

The outer circle of LED lights on Perspex’s panel are its NORMAL LED’s.
Perspex’s NORMAL LED’s display up to sixteen colors to show which signals are
the same (normalled) and which signals are different. The channels that contain
the same signal are identified with the same color on the ring of NORMAL LED’s.

### CAPACITANCE VANE LED 1 through CAPACITANCE VANE LED 16

The inner circle of LED lights on Perspex’s panel are its CAPACITANCE VANE
LED’s. As the capacitance vane in the multiplexer drum passes by each channel’s
input vane, the channel’s CAPACITANCE VANE LED is illuminated. The CAPACITANCE
VANE LED’s are at full brightness when the capacitance vane is exactly aligned
with the channel’s input vane, and the lights fade in or out as the capacitance
vane moves toward or away from each input vane.

### OUT 1 through OUT 4

The Perspex module sends four identical copies of its output channel to the OUT
1, OUT 2, OUT 3, and OUT 4 output jacks. The output signals are clamped at -10.0
volts and +10.0 volts for safety.

Acknowledgements
----------------

In February of 2018, Paul Bristow asked on the [VCV Rack Official Facebook
group](https://www.facebook.com/groups/vcvrack/) if anyone had created a module
with the key functions of the BBC Radiophonic Workshop’s Crystal Palace, and if
not would anyone like to try. I agreed to take on the project, and initial
versions were developed and reviewed by Paul from February through April. The
almost-ready-for-release version was finished in September. Paul has been
enormously patient and generous with his time as I worked the kinks out of
Perspex, and I am very grateful for his guidance.

Members of the [VCV Rack – Plugin Developers Facebook
group](https://www.facebook.com/groups/2035785263299933/), including Andrew
Belt, Lars Bjerregaard, Eric Sterling, Jeremy Wentworth, David O'Rourke, and
Clément Foulc very kindly answered my programming questions. Thanks for your
assistance and encouragement, everyone!

Finally, thanks to Dave Young for the invention and construction of the original
Crystal Palaces, and to Brian Hodgson and the other members of the BBC
Radiophonic Workshop for their unique creations using the devices. The BBC
Radiophonic Workshop team has uniquely enriched my life, and I am so grateful
for their creativity and imagination.

References
----------

The development of the Crystal Palace and other devices by Dave Young is
documented in the “Early Days” article by Ray White on his *BBC Radiophonic
Workshop: An Engineering Perspective* at whiteflies.org, retrievable from
<https://whitefiles.org/rws/r02.htm>.

Ray White’s images collection at <https://whitefiles.org/rwg/> contains numerous
photos of the Crystal Palace, with explanatory captions.

The book, *Special Sound: The Creation and Legacy of the BBC Radiophonic
Workshop*, by Louis Niebur (Oxford University Press, 2010) is a fascinating
account of the Workshop, and includes brief mentions of Dave Young’s Crystal
Palace.

The Radio New Zealand program, “These Hopeful Machines (03 Sep 2013),” includes
an interview with Mark Ayers describing the Crystal Palace, as well as a sound
clip of the device in use. You can listen to the Crystal Palace segment of the
program at
<https://www.radionz.co.nz/concert/programmes/hopefulmachines/audio/20143127/outtake-the-crystal-palace>.

Brian Hodgson’s soundtrack to *Doctor Who: The Krotons* is available on CD and
Digital Download from Silva Screen Records. Information is available at
<http://www.doctorwhomusic.com/new-classic-who-releasethe-krotons/> and the
soundtrack can be purchased through retailers. This disc is a favorite of Paul’s
and is definitely worth a listen!

*Electronic Sound* magazine issue 43, featuring the BBC Radiophonic Workshop’s
60th Anniversary performance at the Royal Albert Hall on May 26, 2018, includes
mentions of the Crystal Palace. The print issue is available from
<https://electronicsound.co.uk/product/issue-43/> for a limited time.

The Science Museum Group's page, ‘Crystal Palace’ Capacitive Fader used in BBC 
Radiophonic Workshop, has excellent color photos of the Crystal Palace (object 
number 2012-5118/242/9) in the BBC Heritage Collection at 
<https://collection.sciencemuseumgroup.org.uk/objects/co8241549/crystal-palace-capacitive-fader-used-in-bbc-radiophonic-workshop-sound-device>.

Changes
-------

### Version 0.6.1.8

Initial public release through the [VCV Rack
Plugins](https://vcvrack.com/plugins.html) page.

### Version 1.0.0

Updated for VCV Rack verion 1.0. Released through the [VCV Rack
Plugins](https://vcvrack.com/plugins.html) page.  Compiled with Rack-SDK v1.06.

### Version 2.0.0

Updated for VCV Rack verion 2.0. Released through the [VCV Rack
Plugins](https://vcvrack.com/plugins.html) page.  Compiled with Rack-SDK v2.2.3.
