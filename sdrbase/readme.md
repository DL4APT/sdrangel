<h1>Main Window interface</h1>

<h2>Multi device support</h2>

Starting with version 2 SDRangel supports several sampling devices simultaneously. A set of tabs is dedicated to each device marked R0, R1, R2... The tabbed windows are:

  - Sampling devices (1)
  - Sampling devices control (2)
  - Spectrum display control (3)
  - Channels (4)
  - Spectrum from device (5)

![Main Window nulti device support](../doc/img/MainWindow_tabs.png)

The sampling devices tab (1) acts as a master and when one of its tabs is selected all other tabs are selected accordingly i.e. all R0s, all R1s, etc... in tabs (2), (3), (4) and (5)

In each slave tab group (2), (3), (4) and (5) an individual tab corresponding to one device can be selected without affecting the selection of the other tabs. This way you can sneak peek into another spectrum or channel goup without affecting the display of other tabbed windows.

<h2>Main areas</h2>

![Main Window interface](../doc/img/MainWindow_general.png)

<h3>1. Main menu</h3>

The following items are presented hierarchically from left to right:

  - File:
   - Exit (shortcut Ctl-Q): Exit the program
  - View:
   - Fullscreen (Shortcut F11): Toggle full screen mode
  - Acquisition:
   - Add device: adds a new sampling device tab set to the device stack (last position)
   - Remove device: removes the last sampling device tab set
  - Window: presents the list of dockable windows. Check to make it visible. Uncheck to hide. These windows are:
   - Sampling devices control: control of which sampling devices is used and add channels
   - Sampling devices: the sampling devices UIs
   - Spectrum display: the main spectrum displays (output from the sampling devices)
   - Presets: the saved presets
   - Channels: the channels active for each device
  - Preferences:
   - Audio: opens a dialog to choose the audio output device
   - DV serial: if you have one or more AMBE3000 serial devices for AMBE digital voice check to connect them. If unchecked DV decoding will resort to mbelib if available else no audio will be produced for AMBE digital voice
  Help:
  - Laoded Plugins: shows details about the loaded plugins (see next)
  - About: current version and blah blah.    

<h3>Loaded plugins display</h3>

When clicking on Help -> Loaded Plugins from the main menu bar a dialog box appears that shows information about the plugins loaded in SDRangel:

![Main Window loaded plugins](../doc/img/MainWindow_loadedPlugins.png)

<h4>Name</h4>

Plugin display name. Tells briefly what this plugin is about.

<h4>Version</h4>

Starting with SDRangel version 2.0.0 this is the SDRangel version when the plugin was last updated.

<h4>GPL</h4>

Tells if the plugin is under GPL license.

<h4>Expansion</h4>

The plugin entry can be expanded or collapsed using the caret on the left. When expanded it shows more information about the copyright of the author and locations on the web where the plugin can be found. In all cases this is just here.

<h4>OK button</h4>

Click here when done to dismiss the dialog.

<h3>2. Sampling devices</h3>

This is where the plugin GUI specific to the device is displayed. Control of one device is done from here. The common controls are:

![Sampling Device common](../doc/img/SampleDevice_common.png)

<h4>2.1. Start or stop acquisition</h4>

  - When a play icon is displayed with a grey background the device is not operational
  - When a play icon is displayed with a blue background the device is ready to start
  - When a square icon is displayed with a green background the device is currently running
  - When a play icon is displayed with a red background there is an error and a popup displays the error message. An Error typically occurs when you try to start the same device in more than one tab.
  
<h4>2.2. Record I/Q</h2>

This is the I/Q from device record toggle. When a red background is displayed the recording is currently active.

<h4>2.3. Device sampling rate</h4>

This is the sampling rate in kS/s of the I/Q stream extracted from the device after possible decimation. The main spectrum display corresponds to this sampling rate.

<h4>2.4. Center frequency</h4>

This is the current center frequency in kHz with dot separated thousands (MHz, GHz). On devices for which frequency can be directly controlled (i.e. all except File Source and SDRdaemon) you can use the thumbwheels to set the frequency. Thumwheels move with the mouse wheel when hovering over a digit and when a digit is selected by clicking on it you can also use the arrows to move the corresponding thumbwheel.

<h4>Additional inputs</h4>

Most devices will also present an interface to control automatic DC removal and I/Q imbalance and also a control of the LO correction in ppm.

  - Example1: ![Sampling Device corr 1](../doc/img/SampleDevice_corr01.png)
  - Example2: ![Sampling Device corr 2](../doc/img/SampleDevice_corr02.png)

<h3>3. Sampling devices control</h3>

This is where the sampling device for one device set is selected and the channel plugins are instantiated.

![Sampling Devices control](../doc/img/MainWindow_SDControl.png)

<h4>3.1. Sampling device selector</h4>

Use this combo box to select one sampling device

<h4>3.2. Sampling device selection confirmation</h4>

Use this push button to confirm the selection and change the sampling device

<h4>3.3. Channel selector</h4>

Use this combo box to select a channel plugin to create a new channel

<h4>3.4. Add a new channel</h4>

Use this push button to add a new channel with the selected plugin

<h3>4. Spectrum display control</h3>

These are the controls of the main spectrum display in (7). Please refer to the spectrum display documentation (TBD) for details.

<h3>5. Presets</h3>

This is a tree view of the saved presets. Presets record the channels setup and a copy of the settings of each sample source that has been used when saving this preset. Thus you can use the same channel arrangement with various devices having their particular setup.

![Main Window presets view](../doc/img/MainWindow_presets_view.png)

<h4>5.1. Preset selection</h4>

You select a preset by clicking on its line in the tree view. All actions (5) will be done relative to this preset.

<h4>5.2. Group</h4>

You can organize your presets into groups. Groups can be collapsed or expanded by using the caret icon on the left.

<h4>5.3. Center frequency</h4>

The center frequency used in this preset is displayed here.

<h4>5.4. Preset name</h4>

You can give a name to your preset. Names need not to be unique.

<h4>5.5. Preset control or actions</h4>

The controls are located as icons at the bottom of the window: 

![Main Window presets](../doc/img/MainWindow_presets.png)

<h5>5.5.1. New preset</h5>

Click on this icon to create a new preset with the current values in the selected sample device tab (Main window: 2).

<h5>5.5.2. Update preset</h5>

Click on this icon to create a update the selected preset with the current values in the selected sample device tab (Main window: 2). Please note that this does not save the preset immediately on disk to save presets immediately you need to use the next icon.

<h5>5.5.3. Save presets</h5>

Presets are saved to disk automatically at exit time you can however request to save them immediately using this icon.

<h5>5.5.4. Export preset</h5>

Using the previous icon presets are saved globally in a system dependent place. Using this icon you can export a specific preset in a single file that can be imported on another machine possibly with a different O/S. The preset binary data (BLOB) is saved in Base-64 format.

<h5>5.5.5. Import preset</h5>

This is the opposite of the previous operation. This will create a new preset in the selected group or the same group as the preset being selected.

<h5>5.5.6. Delete preset</h5>

This deletes the selected preset. It takes no action if a group is selected.

<h5>5.5.7. Load preset</h5>

Applies the selected preset to the current device set (source and channel plugins).  

<h3>6. Channels</h3>

This area shows the control GUIs of the channels curently active for the device. When the preset is saved (as default at exit time or as a saved preset) the GUIs are ordered by increasing frequency. If presets share the same frequenccy they are ordered by their internal ID name. Thus new channel GUIs will appear ordered only when reloaded.

Details about the GUIs can be found in the channel plugins documentation which consits of a readme.md file in each of the channel plugins folder (done partially).

<h3>7. Spectrum from device</h3>

This shows the spectrum in the passband returned from the sampling device possibly after decimation. The actual sample rate is shown in the device control at the left of the frequency display (2.3)

The spectrum display is cotrolled by the display control (4).
 
<h3>8. Status</h3>

![Main Window status](../doc/img/MainWindow_status.png)

<h4>8.1. SDRangel version</h4>

Self explanatory

<h4>8.2. Qt version</h4>

Qt version with which this copy of SDRangel was compiled.

<h4>8.3. System</h4>

Pretty print of the system in which SDRangel is running.

<h4>8.4. Local date</h4>

Local date according to system clock

<h4>8.5. Local time</h4>

Local time according to system clock followed by the time zone code.

