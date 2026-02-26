# Voice Assistant "Roz"

A voice assistant with a graphical interface in Python. It constantly listens to the microphone, activates upon hearing the name ("Роз" or "Roz"), and executes commands (opening applications/websites, Google search, telling the time, playing music, closing apps). You can add custom commands via a user-friendly interface or console.

## Requirements

- Python 3.7 or higher
- Microphone
- Internet connection (for Google Speech Recognition)

## Installation

1. Make sure Python is installed. Check:
python --version

text

2. Install the required libraries:
pip install speechrecognition pyttsx3 pyaudio flet

text
If you encounter issues with PyAudio:
- **Windows**: download the appropriate wheel from [https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyaudio](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyaudio) and install with `pip install <file.whl>`.
- **Linux**: `sudo apt-get install portaudio19-dev python3-pyaudio`
- **macOS**: `brew install portaudio && pip install pyaudio`

## Running

Save the code to a file, e.g., `roz.py`, and run:
python roz.py

text
A window with three tabs will open: **Main**, **Console**, **List**.

## Usage

### Voice Control

1. Say **"Роз"** (or "Roz").
2. The assistant will reply **"Слушаю"** (Listening).
3. Speak a command:
   - **"open notepad"** – opens Notepad.
   - **"open youtube"** – opens YouTube in your browser.
   - **"find weather in Moscow"** – performs a Google search.
   - **"What's time is it?"** – tells the current time.
   - **"play music"** – plays a random music file from `~/Music`.
   - **"close calculator"** – attempts to close the application (by process name).
   - **"bye"** – exits the assistant.

### Console Tab

In the console tab, you can type text commands. If the command starts with a system keyword (`help`, `pink`, `pank`, `add`, `remove`, `list`, `clear`, `exit`), it's treated as a control command. Otherwise, it's executed as a regular voice command (e.g., "открой блокнот").

System commands:
- `help` – show help.
- `pink` – enable voice listening (after disabling).
- `pank` – disable voice listening (the assistant stops reacting to its name).
- `add <command> <path/url> [display_name] [type] [trigger_type]` – add a custom command.
   - `type`: `app` (application) or `site` (website), default `app`.
   - `trigger_type`: `prefix` (standard, after "открой") or `exact` (exact phrase), default `prefix`.
   - Example: `add steam "C:\Program Files\Steam\Steam.exe" "Steam" app prefix`
   - Example: `add "i want to play" "C:\Program Files\Steam\Steam.exe" "Steam" app exact`
- `remove <command>` – remove a command.
- `list` – list all added commands.
- `clear` – clear the console log.
- `exit` – exit the program.

### List Tab (Adding Custom Commands)

Here you can add and remove your own commands via the graphical interface.

1. Choose **command type**:
   - *Standard (open/launch)* – the command will be triggered by the phrase "open X", where X is the voice command you specify.
   - *Exact phrase* – the command triggers when the spoken phrase exactly matches (e.g., "i want to play").
2. Enter the **voice command** (required). For example, `steam` or `i want to play`.
3. Optionally, enter a **display name** (for nicer appearance in the list). If omitted, the voice command is used.
4. Specify the **file path** (for applications) or **URL** (for websites). For applications, you can click "Browse".
5. Choose **item type**: Application or Site.
6. Click **Add**.

The item will appear in the list. When you say "Роз, open steam" (for standard) or "Роз, i want to play" (for exact), the specified application or website will launch.

To delete an item, select it in the list and click "Remove selected" (simplified – use the `remove` console command).

## Command Examples

| What to say                          | What happens                            |
|--------------------------------------|-----------------------------------------|
| Roz, open notepad                    | Notepad launches                        |
| Roz, open youtube                    | YouTube opens in browser                 |
| Roz, search borscht recipe           | Google search                            |
| Roz, what time is it                 | Tells the current time                   |
| Roz, play music                      | Plays a random track from `~/Music`      |
| Roz, close calculator                | Attempts to close Calculator             |
| Roz, bye                             | Exits the program                        |

## Troubleshooting

### 1. PyAudio installation fails
   - **Windows**: download the wheel from [lfd.uci.edu](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyaudio) and install manually.
   - **Linux**: `sudo apt-get install portaudio19-dev python3-pyaudio`
   - **macOS**: `brew install portaudio && pip install pyaudio`

### 2. Speech recognition doesn't work
   - Ensure you have an internet connection.
   - Check if your microphone works in other applications.
   - Increase microphone volume.

### 3. Application won't open on command
   - Verify the file path in settings (especially if entered manually). The path must be correct.
   - For applications in PATH (e.g., `calc.exe`), you can just use the name.

### 4. Error "module 'flet' has no attribute ..."
   - Make sure you have the latest Flet: `pip install --upgrade flet`
   - If the error persists, install version 0.24.1: `pip install flet==0.24.1`

### 5. Program cannot access microphone
   - Run as administrator (on some systems microphone access requires elevated privileges).

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute it.

## Contact

If you have any questions or suggestions, please open an issue on GitHub or contact the author.
