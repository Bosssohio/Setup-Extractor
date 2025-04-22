# TestingInstallers

TestingInstallers is a Windows Forms application designed to handle the installation, repair, and uninstallation of a software package. It provides a user-friendly interface for managing the application's lifecycle.

## Features
- **Installation**: Extracts and installs the required files to a specified directory.
- **Repair**: Allows users to repair the installation by re-extracting files.
- **Uninstallation**: Removes all installed files and directories.
- **Customizable Paths**: Users can select custom installation or repair paths.

## Requirements
- **.NET Framework**: 4.7.2
- **C# Version**: 7.3
- **Operating System**: Windows

## Installation
1. Clone or download the repository.
2. Open the solution in Visual Studio.
3. Build the project to ensure all dependencies are resolved.
4. Run the application. If it's the first time, the installation process (`Form1`) will start.

## Usage
- **First Run**: The application will prompt for installation. Select a directory and complete the process.
- **Subsequent Runs**: The application will open the management interface (`Form2`) for repair or uninstallation.

## File Overview
- **`Program.cs`**: Entry point of the application. Handles the logic for determining whether to run the installer (`Form1`) or the management interface (`Form2`).
- **`Form1.cs`**: Handles the installation process, including extracting files and logging installation details.
- **`Form2.cs`**: Provides options for repairing or uninstalling the application.
- **`Resources.resx`**: Contains embedded resources, such as the installation package.

## How It Works
1. On the first run, the application checks for the `install_completed.flag` file.
2. If the flag file is missing, the installation process (`Form1`) starts.
3. After installation, the flag file is created, and the application exits.
4. On subsequent runs, the application opens the management interface (`Form2`).

## Troubleshooting
- **"Install skipped" Message**: This appears if the installation process is canceled.
- **Repair Errors**: Ensure the selected repair path is valid and accessible.
- **Uninstallation Errors**: Verify that the installation log file exists in the specified directory.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments
- Developed using Visual Studio with .NET Framework 4.7.2.
- Icon and resources included in the project are for demonstration purposes.
