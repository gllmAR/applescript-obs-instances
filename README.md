# applescript-obs-instances

## Overview
This project provides an AppleScript script to launch multiple independent instances of OBS Studio (Open Broadcaster Software) on macOS, each with its own configuration, profile, and WebSocket port. This is useful for users who need to run several isolated OBS environments simultaneously.

## Main Script: `apple_script_obs_instances`

### Functionality
- **App Path & Name Extraction:**
  - Retrieves the full POSIX path to the running app.
  - Extracts the app's name (e.g., `OBS-2`) and parses the instance index from the name.
- **Dynamic Configuration:**
  - Constructs unique profile, collection, and configuration directory names based on the instance index.
  - Assigns a unique WebSocket port for each instance (starting from 4455).
- **OBS Launch Command:**
  - Builds a shell command to launch a new instance of OBS Studio with the specified parameters:
    - `--multi` and `--portable` for isolated operation
    - Custom profile, collection, and config directory
    - Unique WebSocket port
  - Executes the command to start OBS.

### Key Variables
- `appPath`: Full POSIX path to the app.
- `appName`: Name of the app, used to extract the instance index.
- `appIndex`: Numeric index for the instance (parsed from app name).
- `profileName`, `collectionName`, `configDir`: Unique identifiers for each instance.
- `wsPort`: WebSocket port (4455 + instance index).
- `shellCommand`: The full command to launch OBS with the above parameters.

### Usage
- Duplicate the app bundle and rename it (e.g., `OBS-1.app`, `OBS-2.app`).
- Each renamed app will launch an independent OBS instance with its own settings and port.

## Limitations
- Designed for macOS and AppleScript.
- Assumes OBS is installed and accessible via the `open -n -a 'OBS'` command.
- The script is not directly usable on Linux or Windows without adaptation.

## File List
- `apple_script_obs_instances`: Main AppleScript script.
- `README.md`: Documentation and usage instructions.

## References
- [OBS Studio](https://obsproject.com/)
- [AppleScript](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptLangGuide/introduction/ASLR_intro.html)

---

For further customization or cross-platform support, consider adapting the script logic to Bash or Python for Linux/Windows environments.
