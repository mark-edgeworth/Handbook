<h2 id="mbed-studio">Arm Mbed Studio</h2>

Arm Mbed Studio is a local development environment for Mbed OS projects. This document helps Mbed OS developers use Mbed Studio to code, run, debug and deploy Mbed OS programs to Mbed Enabled devices. The Mbed Studio project is based on the Eclipse framework and extends Eclipse’s IDE capability to provide a more focused experience for developing with Mbed OS. In particular, it allows users to develop and deploy code offline. It also provides access to existing online resources.

### Current status and downloads

Mbed Studio is currently in closed alpha. You can [request access here](https://os.mbed.com/studio/) if you're happy to provide feedback. During this phase, some features are still in progress, and there will be frequent updates to the product.

### Getting started

This section shows the steps of creating, exploring, running and debugging an example project packaged with Mbed Studio. After reading it, you will have a better understanding of how you can use Mbed Studio to develop for Mbed OS. Start Mbed Studio and follow the steps below.

#### On startup

When you launch Mbed Studio, you see a login screen (unless you're using an internal release), which requires you to sign in with your Mbed username and password. Sign in with your Mbed credentials. If you're an authorised alpha user you can continue through to the workspace.

#### Creating a new project based on an example

When you arrive in your workspace, it's empty - clean, white and lacking in programs. It's time to start populating it.

The first step is to create a project based on the included `mbed-os-example-blinky` example. You can do this using the Mbed Studio menu or using the context menu in the Mbed Projects view of Mbed Studio.

To use the context menu, right-click (Ctrl-click) inside the Mbed Projects view, and then select `New > Mbed OS Application`. To do the same through the menu, click `File > New > Mbed OS Application` to activate the New Project wizard.

Now, create a new project through the activated New Project wizard. Select the `From Supplied Example` radio button, and then select the `mbed-os-example-blinky` example from the list of examples. Continue through the wizard by clicking the `Next` button.

Fill in the project name (you can be creative or just use the default example name), and update the location to match (`/path/to/project_name` for example: `/eclipse-ws/mbed-os-example-blinky`). Mbed Studio uses the project name, not the location name, to name created binaries. Once these steps are complete, click the `Finish` button in the lower part of the wizard window.

Additionally, you can create a blank project with the `Empty Project` radio button. As a result, you can click `Finish` without continuing, which creates a blank project.

Mbed Studio now begins to create the project in the workspace and shows its progress on the final screen of the wizard. Once complete, you can see the project in your workspace within the `Mbed Projects` view.

#### Explore or edit the project

Mbed Studio provides support for formatting, syntax highlighting, locating files, comparing files and navigating to lower level code, such as pin definitions for your target hardware. For a more general look at the features provided by Eclipse, consult the [Eclipse](http://help.eclipse.org/neon/index.jsp) online help documentation.

Now, there is a project located under the `Active Project` node in the `Mbed Projects` view with the name `mbed-os-example-blinky` (or whatever project name you provided earlier). Clicking the triangle next to the project expands its contents and reveals the project’s current files and directories.

Double-click on the `main.cpp` file to open it in Mbed Studio’s editor area. This file includes the code needed to blink an LED. If you haven’t done so already, connect an [Mbed Enabled board](https://os.mbed.com/platforms/) to your machine. Mbed Studio detects the board and prompts you with a dialog asking to switch targets. Accept this, and you are ready to run the example.

#### Running the project

This section covers the necessary steps of building and running the project, so the program deploys and runs a connected board. Mbed Studio must recognize the board for the instructions in the Run section to work.

##### Build

Before you can run the program, Mbed Studio needs to build a binary using a compiler. For the alpha version of Mbed Studio this compiler is GCC. There are multiple ways to start a build, but the easiest is to click the build icon.

Alternatively, you can right-click (Ctrl-click) on the project in the `Mbed Projects` view and then select `Build Project`. You can also use the menu by choosing `Project > Build Project`. Both begin to build a binary that you can deploy.

Alternatively, you can choose to build the project automatically through the menu by choosing `Project > Build Automatically`. This tells Mbed Studio to build the projects in the workspace whenever needed. After the build, an `mbed-os-example-blinky.bin` (or `<project name>.bin`) file is ready to deploy.

##### Building within Mbed Studio

Mbed Studio uses the tools built into Mbed OS to determine what builds and where the output of a build goes. The build tools build on request or (if the `Project > Build Automatically` option is checked) when you change and save a source file. The build operation only builds components that have changed and does nothing if nothing changed. 

The aim is to maintain a system that is always in a built state, providing rapid error feedback to developers as they make changes.

Under some circumstances (in particularly large projects, or when the target device changes frequently), you may wish to turn off automatic builds and build the active project on request. To do this, select Build from the project right-click menu.

##### Run

Now that you have built the `mbed-os-example-blinky project`, you can run it. Running a project consists of several phases, which are abstracted if you click the green run icon.

The Mbed Studio run phases are:

- Locate or create a suitable binary.
- Deploy the binary to the target.
- Reset target, causing the deployed program to run.

Although you manually built the project in the previous section and learned how to build a project in Mbed Studio, it wasn’t necessary before running. That’s because Mbed Studio checks that there is a binary for the currently selected target. If there isn’t one, Mbed Studio begins a compilation to create the binary. If there is a binary and there are no recent changes (build automatically option is on), Mbed Studio uses the existing binary to run the project.

Once Mbed Studio has a binary of the Mbed OS program, it deploys that binary to the currently selected target and resets the target, so the program begins to run.

To make it happen, click the green run icon to launch the default run configuration for your connected development board.

Alternatively, open the context menu (right-click, ctrl-click) on the `mbed-os-example-blinky` project and select `Run As > Run Configurations...` from the menu. You can also use the menu by selecting `Run > Run Configurations`.

In the `Run Configurations` window, right-click on `Mbed Deploy`, and select `New` to create an `Mbed Deploy` run configuration. This creates the run configuration you need to populate with details of your project and target. For project (if everything isn’t already populated), click `Choose`, and select the `mbed-os-example-blinky` project. The binary Mbed Studio builds fills in automatically. If you used a different project name, the binary name reflects that. Finally, click the Refresh button to ensure that the current target board’s ID updates if it hasn’t already.

After you have configured everything, click on the Apply button and then on the Run button.

Watch the primary LED on your connected target begin to blink!

#### Debugging

Now that you have learned the basics of Mbed Studio, it is time to learn how to debug projects within the IDE. There is a simplified debug configuration specifically for easy debugging of Mbed OS projects. There are also additional configurations for more advanced debugging. This section covers the Mbed OS debug configuration, as well as the advanced PyOCD GDB debug configuration.

##### Simple debugging

To begin debugging, click the bug icon, which launches the default debug configuration.

Alternatively, you can create the debug launch configuration and then begin debugging. To create a debug launch configuration, right-click on a project and select `Debug As... > Debug Configurations` from the context menu.

Click `Choose...` next to the project textbox, and select the project you wish to debug if it isn’t already populated. After that, connect a board, and the project is ready to debug. The Mbed Debug launch configuration prepopulates the PyOCD GDB server and the GDB client to locations to the internal Mbed Studio tools. Select the Debug button in the lower right portion of the window to start debugging.

Mbed Studio automatically switches into the Mbed Debug perspective when debugging with the Mbed Debug launch configuration. The project also breakes on a default break point.

##### Advanced debugging

If you want more control over the options regarding debugging, this section is for you. This section describes how to create a PyOCD GDB debug configuration. This configuration allows you to change more settings, such as ports and executable locations for the GDB client and server.

To begin debugging, create the debug launch configuration and set some variables. (You may use your own values if you don’t want to use the default provided here.) To create a debug launch configuration, as before, right-click on a project, and select `Debug As... > Debug Configurations` from the context menu.

A window for the debug configurations appears. Select the `GDB PyOCD Debugging` category, and create a new launch configuration. You can click the new icon (a page with a `+` in the upper right corner), or right-click on the category and select `New`.

Next, configure the binary you want to use for debugging. This is the `.elf` file located within the project directory and inside `BUILD/<target>/GCC_ARM`. Currently, this is configured manually, so switching to a different target to run the same project requires you to update this field in the debug configuration. 

The next step is to configure the location of the executables for the PyOCD GDB Server and the GDB Client on the Debugger tab within the debug configuration. These should be set to the executables located within Mbed Studio’s tools directory which is located at:

`/eclipse-ws/mbed-studio-ws/tools`

Alternatively, and at your own risk, you may select executables from locations elsewhere on your machine.

On *nix machines, the two bundled executables are located at:

`/eclipse-ws/mbed-studio-ws/tools/python/bin/pyocd-gdbserver`
`/eclipse-ws/mbed-studio-ws/tools/gcc-arm/bin/gcc-arm-none-eabi-gdb`

On Windows machines, the two bundled executables are located at:

`\eclipse-ws\mbed-studio-ws\tools\python\Scripts\pyocd-gdbserver.exe`
`\eclipse-ws\mbed-studio-ws\tools\gcc-arm\bin\gcc-arm-none-eabi-gdb.exe`

When you have configured everything, select `Apply` in the lower right side of the panel, and the click the blue Debug button just below that.

### Help

This section outlines known issues and provides answers to common questions.

#### Glossary

##### Workspace

Mbed Studio automatically sets up the workspace. Use it to keep track of settings and user preferences for all of the projects you open in Mbed Studio.

##### Project

A project is a group of associated files, directories and settings. The `Mbed Projects` view lists these projects. In Mbed Studio, each project represents an Mbed OS program or an Mbed OS library. An Mbed Studio project can also represent a program that includes libraries, as well.

##### View

In Mbed Studio, a view is a window that has a label, and sometimes options, specific to that window. Examples are the editor, `Mbed Projects`, `Console` and `Outline`.

##### Perspective

A perspective is a collection of views, which group functionality in Eclipse. An example of a perspective is the debug perspective.

##### Program

This term denotes a project that contains code that runs on an Mbed Enabled device.

##### Library

This term denotes a project that contains code meant to be included in other Mbed OS programs.

### Known issues

This section lists known issues that currently exist in Mbed Studio.

#### General

Currently, Mbed Studio does not communicate with ST boards because they don’t use DAPLink by default.
Workaround: None

#### Mac

When CDT (C/C++ Developer Tooling) performs a build, it tries to use the system GCC. If it is not present, Mac OS X prompts to install the Xcode command-line tools.
Workaround: None. Follow the prompts to install the command-line tools, and restart Mbed Studio.

#### Linux

Mbed Studio does not currently pick up target boards in the Linux version. This is an issue with the detection of USB. Interacting with boards is not possible currently.
Workaround: None

#### Windows

Using the product update functionality in Eclipse returns a timestamp error.
Workaround: This error does not prevent the product from successfully updating.

### FAQ

This section includes common questions and answers.

Q: Do I need to install Java, or a compiler?
A: No, Mbed Studio bundles its own Java Runtime Environment and other tools required for its operation.
