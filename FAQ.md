# FAQ

## Where is the "Rack user folder"?

The Rack user folder stores data readable/writable by Rack.
You can open it by choosing `Help > Open user folder` in the Rack [menu bar](MenuBar.html), or by navigating to

- MacOS: `Documents/Rack/`
- Windows: `My Documents/Rack/`
- Linux: `~/.Rack/`

When running Rack in development mode, it is your current working directory instead.

## Will Rack be ported to iOS or Android?

It is not planned. There are many issues with such a project.

- Technical:
	- Tablet and phone users don't normally use mice, so a touch driver would need to be written. If GLFW is still used, [touch support](https://github.com/glfw/glfw/issues/42) would need to be added to the library.
	- There is no user-managed filesystem on iOS, and forcing users to mess with the filesystem is bad UX on Android, so plugin folders and patch files would need to be managed entirely by Rack itself.
	- RtAudio and RtMidi don't have iOS Core Audio/MIDI or Android HAL/OpenSL ES backends, so they would need to be added and tested.
	- Apple does not allow apps distributed through the store to download and execute code, so either all plugins would need to be included in the distributable, or it could only be distributed on jailbroken iOS devices, which is an absurd user requirement.

- Business:
	- Such a port would be expensive to develop, so it would need to be sold commercially. Some plugins (proprietary, GPL, etc) would need special licensing agreements in order to be included in the package. Some plugins would increase the cost of the product if included in the package. Others would simply be omitted from the third-party plugin collection.
	- The friction for a developer to build and test their plugins on iOS/Android is significantly higher than the three desktop OS's, which may decrease their willingness to develop Rack plugins.
	- When serving an app on the App Store or Google Play, Apple and Google are not obligated to continue serving an app and may remove it at will or change policies on a whim that can disrupt VCV's business model. This would place a large risk upon VCV.

## Is VCV Rack available as a VST/AU/AAX plugin for DAWs?

VCV Rack can be fully considered a DAW itself rather than a "synthesizer plugin", so Rack is a standalone application.
However, due to overwhelming user demand, a new product called *VCV Rack for DAWs* will be available as a 64-bit VST2 plugin for around $99 shortly after Rack v2 is released.
VST3/AU/AAX/LV2 versions might be released afterwards, but this is not yet confirmed.
All Rack v2 plugins will be compatible with the plugin version of Rack.
The standalone version of Rack v2 will continue to be free/open-source.

## What was VCV Bridge?

[VCV Bridge](https://github.com/VCVRack/Bridge) was an experimental project for transferring audio/MIDI between VCV Rack and another DAW via a VST2/AU plugin.
It relied on [inter-process communication (IPC)](https://en.wikipedia.org/wiki/Inter-process_communication) between Rack (server) and the DAW plugin (client), similar to [ReWire](https://en.wikipedia.org/wiki/ReWire_(software_protocol)).
Because real-time IPC of audio cannot be achieved on non-[real-time operating systems](https://en.wikipedia.org/wiki/Real-time_operating_system), it was never intended as more than a fun experiment, and the project was concluded a month after development started.
One could say the experiment "failed", but its purpose was primarily to see how much it would fail.
The conclusion was that it was not reliable enough for the majority of users.
VCV Bridge was deprecated in July 2018 and is now unsupported.
The Bridge VST2/AU plugin was removed in Rack 1.0 (although it can be found in [earlier Rack packages](https://vcvrack.com/downloads/)), and the Bridge audio/MIDI driver will be removed in Rack 2.0.

## Does VCV Rack work with touch screens?

Rack's window library GLFW does not support [touch input](https://github.com/glfw/glfw/issues/42) yet, so Rack relies on the operating system to control the mouse cursor using the touch screen.
This means that multi-touch gestures do not work.
However, you can disable "View > Lock cursor while dragging" in the menu bar to prevent Rack from grabbing the mouse cursor when interacting with knobs.
