# SuperInstaller

## Overview

SuperInstaller is a C# Windows Forms application designed to simplify the installation process for your software.  It creates a single, self-contained executable (`Installer.exe`) that contains all the necessary files and logic to install your application.  This approach offers a streamlined and portable installation experience.

## Key Features

* **Single-File Installation:** Packages all installation files into a single, self-contained `Installer.exe`.
* **Embedded ZIP Archive:** Embeds a ZIP archive containing your application's files within the `Installer.exe`.
* **Dynamic Uninstaller Generation:** Generates an `Uninstaller.exe` at installation time using Roslyn (C# compiler).
* **Customizable Installation Path:** Allows the user to select the installation directory.
* **Installation Logging:** Creates an `InstallationLog.txt` file in the installation directory.
* **Progress Tracking:** Provides a progress bar and output messages during installation.
* **Resource Management:** Uses `Resources.resx` to store the embedded ZIP archive and uninstaller code.

## How It Works

1.  **Preparation:**
    * You, as the developer, place your application's files into a directory.
    * You add the application files to a ZIP archive.
    * You embed this ZIP archive into the `SuperInstaller` application's resources (`Resources.resx`).
    * The uninstaller C# code is also stored in `Resources.resx`.
2.  **Installation:**
    * When the user runs `Installer.exe`:
        * The embedded ZIP archive is extracted to the user-selected directory.
        * An `Uninstaller.exe` is dynamically generated using Roslyn and placed in the same directory.
        * An `InstallationLog.txt` file is created.
3.  **Uninstallation:**
    * The generated `Uninstaller.exe` removes the installed files and the installation log.

## Code Details

The `SuperInstaller` application is primarily contained within the `Form1` class. Here's a breakdown of the key methods:

* **`Form1()`:**
    * Initializes the form, resource manager, and UI elements.
    * Sets the default installation path.
* **`browseButton_Click()`:**
    * Displays a `FolderBrowserDialog` to allow the user to select the installation directory.
* **`button1_Click()`:**
    * Validates the selected installation path.
    * Disables UI elements.
    * Starts the installation process on a background thread using `Task.Run()`.
* **`PerformInstallation()`:**
    * Clears the list box.
    * Retrieves the embedded ZIP archive from `Resources.resx`.
    * Extracts the contents of the ZIP archive to the installation directory.
    * Writes installation details to `InstallationLog.txt`.
    * Generates and compiles `Uninstaller.exe` using Roslyn.
    * Displays a completion message.
    * Handles potential exceptions during the installation process.
    * Re-enables UI elements in the `finally` block.
* **`CompileUninstallerRoslyn(string outputPath)`:**
    * Retrieves the uninstaller C# code from `Resources.resx`.
    * Uses Roslyn to compile the code into an executable file (`Uninstaller.exe`).
* **`FormatFileSize(long bytes)`:**
    * Helper method to format file sizes (bytes, KB, MB) for display.
* **`UpdateOutput(string message)`:**
    * Updates the `listBox1` control with installation progress messages.
* **`button2_Click()`:**
    * Closes the Form.

## Dependencies

* **Microsoft.CodeAnalysis.CSharp:** Used for Roslyn compilation.
* **System.IO.Compression.FileSystem:** Used for handling ZIP archives.
* **System.Windows.Forms:** For the GUI elements.

## Getting Started

1.  **Prerequisites:**
    * Visual Studio (with C# support)
    * Ensure the required NuGet packages (`Microsoft.CodeAnalysis.CSharp`, `System.IO.Compression.FileSystem`) are installed in your project.
2.  **Set up your project:**
    * Create a new Windows Forms project.
    * Design your form.
    * Add a ListBox, a Progress Bar, a TextBox, and Buttons.
    * Add a folder named "Resources" to your project.
3.  **Add your application files:**
    * Place all the files you want to install into a directory.
    * Create a ZIP archive of this directory.
    * Add the ZIP archive to your project's Resources.resx. **Important:** Give it the name "installation\_files" (or change the constant `ZipResourceName`).
    * Add the Uninstaller code to `Resources.resx` and give it the name "UninstallerCode".
4.  **Copy the code:**
    * Copy the code from the "Modified Form1.cs" and paste it into your Form1.cs file.
5.  **Configure:**
    * Make sure the names of the resources match the names used in the code (e.g., `ZipResourceName`, `UninstallerResourceName`).
    * Modify the `embeddedFileResourceNames` array to include the names of the zip files you want to install.
6.  **Build and Run:**
    * Build your project. The resulting `Installer.exe` will be in your `bin\Debug` or `bin\Release` directory. This `Installer.exe` is self-contained and ready to distribute.

## Important Considerations

* **Self-Contained Installer:** The `Installer.exe` that is generated is self-contained. It does not require any other executable to run.
* **Error Handling:** The code includes basic error handling, but you may want to add more robust error logging and user feedback.
* **Uninstaller Code:** The uninstaller code is generated dynamically. Ensure that it correctly removes all installed files and directories.
* **Resource Management:** Properly manage the embedded resources to avoid memory issues.
* **Security:** Be mindful of security implications when generating and compiling code at runtime. Ensure that the embedded resources are from a trusted source.
* **User Interface:** Consider enhancing the user interface with a more professional look and feel.
* **Testing:** Thoroughly test the installer and uninstaller to ensure they function correctly in different environments.
* **Dependencies:** If your application has external dependencies (e.g., DLLs), ensure they are included in the ZIP archive and extracted during installation.
* **Update embeddedFileResourceNames**: Change the string array `embeddedFileResourceNames = { "subterob-v1.0.0.zip" }`; to the name of your zip file in the `Resources.resx`. If you have more than one zip file, add all the names.
* **Change ZipResourceName**: Change the constant `private const string ZipResourceName = "installation_files";` to the name you gave to the zip file in the `Resources.resx`.

## Source Code

* **Coming Soon:** The source code for this project will be made available in a future release.

## Contributing

1.  Fork the repository.
2.  Create a new branch.
3.  Make your changes.
4.  Commit your changes.
5.  Push to the branch.
6.  Create a pull request.
