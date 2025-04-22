# TestingInstallers

TestingInstallers is a Windows Forms application designed to handle the installation, repair, and uninstallation of software packages. It provides a user-friendly interface for managing the application's lifecycle.

## Features
- **Installation**: Extracts and installs files from a ZIP package to a specified directory.
- **Repair**: Re-extracts files to repair the installation.
- **Uninstallation**: Removes installed files and cleans up the Registry.
- **Registry Integration**: Stores installation details (e.g., file paths, version, install date) in the Windows Registry.

## Requirements
- **.NET Framework**: 4.7.2
- **Operating System**: Windows 7 or later

## Installation
1. Clone or download the repository.
2. Open the solution in Visual Studio.
3. Build the project to ensure all dependencies are resolved.
4. Run the application to start the installation process.

## Usage
- **First Run**: The application will prompt for installation. Select a directory and complete the process.
- **Subsequent Runs**: The application will open the management interface for repair or uninstallation.

## File Overview
- **`Form1.cs`**: Handles the installation process, including extracting files and storing details in the Registry.
- **`Form2.cs`**: Provides options for repairing or uninstalling the application.
- **`Resources.resx`**: Contains embedded resources, such as the installation package.

## Registry Keys
The application uses the following Registry keys under `HKEY_CURRENT_USER\SOFTWARE\TestingsInstallers`:
- **`InstallFiles`**: Stores paths of all installed files (semicolon-separated).
- **`InstallPath`**: Stores the installation directory.
- **`Version`**: Stores the version of the application.
- **`InstallDate`**: Stores the installation date and time.
- **`InstalledBy`**: Stores the username of the person who installed the application.

## Uninstallation
1. Open the application and select the "Uninstall" option.
2. The application will delete all installed files and remove the Registry keys.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments
- Developed using Visual Studio with .NET Framework 4.7.2.
- Icon and resources included in the project are for demonstration purposes.

