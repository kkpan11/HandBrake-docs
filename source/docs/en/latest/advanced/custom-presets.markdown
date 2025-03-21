---
Type:            article
Title:           Custom Presets
Project:         HandBrake
Project_URL:     https://handbrake.fr/
Project_Version: Latest
Language:        English
Language_Code:   en
Authors:         [ Scott (s55) ]
Copyright:       2024 HandBrake Team
License:         Creative Commons Attribution-ShareAlike 4.0 International
License_Abbr:    CC BY-SA 4.0
License_URL:     https://handbrake.fr/docs/license.html
---

Custom Presets
=============================

HandBrake comes with many built-in presets which cover the most common use case scenarios. However there are many scenarios and devices that many not be covered.

After you have chosen your preferred settings, you can click the "Save New Preset" button on the main window to create your own preset.

<!-- .system-linux -->
<!-- /.system-linux -->
<!-- .system-macos -->
![macOS Preset Controls](../../images/windows/preset-controls-mac-1.4.0.png "Preset Controls (macOS)")
<!-- /.system-macos -->
<!-- .system-windows -->
![Windows Preset Controls](../../images/windows/preset-controls-win-1.8.0.png "Preset Controls (Windows)")
<!-- /.system-windows -->

When you've pressed this button, you'll see the following window appear:

<!-- .system-macos -->
![macOS Add Preset](../../images/windows/add-preset-mac-1.4.0.png "Add Preset (macOS)")
<!-- /.system-macos -->
<!-- .system-windows -->
![Windows Add Prese](../../images/windows/add-preset-win-1.8.0.png "Add Preset (Windows)")
<!-- /.system-windows -->

Pressing "add" will save a new preset with the details you've entered based on the settings that are currently on the main window. 


## Audio and Subtitles Beavhiours 

Audio and Subtitle settings are special. The preset does not store selected audio and subtitle tracks from the audio or subtitle tabs. It uses rules to automatically select them for each new source or title that you selected.
You can modify these rules by editing the settings on the relevant "selection behaviour" screen.

Please note, these rules do not cover all possible use cases. If the behaviours don't meet your requirements, audio and subtitle tracks will need to be handled manually after you've scanned a source before adding it to the queue.

For more information, please see [Audio and Subtitle Defaults](../workflow/audio-subtitle-defaults.html).

## Default Preset

If you regularly use the same preset, you can make it the default preset that HandBrake starts with by selecting the "Make Default" (macOS) or "Set Current as Default" (Windows) option in the presets menu or by using the preset manager accessed via the toolbar.

## Import and Export

You can export and import presets (singularly or many at a time) from the preset pane for backup or sharing purposes. 

## Preset File Locations

The presets file are stored in the following location: 

- Windows: C:\Users\%Username%\AppData\Roaming\HandBrake\presets.json
- Flatpak: /var/app/fr.handbrake.ghb/config/ghb/presets.json
- macOS: ~/Library/Containers/fr.handbrake.HandBrake/Data/Library/Application Support/HandBrake/UserPresets.json (Note, "fr.handbrake.HandBrake" will be shown as "HandBrake" when viewed in Finder)
