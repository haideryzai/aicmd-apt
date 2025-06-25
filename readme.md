# `aicmd`: Your AI-Powered Linux Command Assistant

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Linux](https://img.shields.io/badge/OS-Linux-informational?style=flat&logo=linux&logoColor=white)](https://www.linux.org/)

## Overview

`aicmd` is a powerful command-line tool that transforms your natural language questions into executable Linux shell commands. Powered by Google's Gemini AI, `aicmd` makes navigating the terminal easier for everyone, from beginners to seasoned users looking for quick command recall. Simply ask what you want to do, and `aicmd` will provide the command.

## Features

* **Natural Language to Command:** Converts plain English queries into precise Linux commands.
* **Gemini AI Integration:** Leverages the advanced capabilities of Google Gemini for accurate translations.
* **Optional Command Execution:** Displays the generated command and gives you the option to run it directly.
* **Secure API Key Management:** Prompts for your Gemini API key on first use and stores it securely.
* **Easy Key Renewal:** Update your API key anytime with a simple command.
* **Beginner-Friendly:** Great for new Linux users to learn commands quickly.
* **Efficiency Boost:** Helps experienced users recall complex or less frequently used commands.

## Installation (For Users)

`aicmd` is designed for Debian/Ubuntu-based Linux systems.

1.  **Ensure Prerequisites:**
    Make sure you have `curl` and `jq` installed on your system. These are usually available by default, but you can install them if needed:
    ```bash
    sudo apt update
    sudo apt install curl jq
    ```

2.  **Add the `aicmd` APT Repository:**
    To allow `apt` to find and install `aicmd`, you need to add its repository to your system.

    First, import the GPG public key used to sign the repository. This ensures the packages you install are authentic and untampered with:
    ```bash
    wget [https://haideryzai.github.io/aicmd-apt/aicmd-apt-repo-key.gpg](https://haideryzai.github.io/aicmd-apt/aicmd-apt-repo-key.gpg) -O /tmp/aicmd.gpg
    sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/aicmd-repo.gpg /tmp/aicmd.gpg
    ```

    Next, add the repository URL to your `sources.list.d`, instructing `apt` where to fetch `aicmd` packages from. **Ensure you use the GitHub Pages URL:**
    ```bash
    echo "deb [signed-by=/etc/apt/trusted.gpg.d/aicmd-repo.gpg] [https://haideryzai.github.io/aicmd-apt](https://haideryzai.github.io/aicmd-apt) stable main" | sudo tee /etc/apt/sources.list.d/aicmd.list > /dev/null
    ```

3.  **Install `aicmd`:**
    Update your package lists to include the new repository, and then proceed with the installation of `aicmd`:
    ```bash
    sudo apt update
    sudo apt install aicmd
    ```

## Usage Examples

Once installed, using `aicmd` is straightforward.

1.  **Basic Usage:** To get a Linux command, simply type `aicmd` followed by your query in double quotes:
    ```bash
    aicmd "how to list all files in the current directory, including hidden ones?"
    ```
    `aicmd` will display the suggested command. It will then ask if you want to execute it (e.g., `Run? [y/N]`).

2.  **First-Time Setup:** The very first time you run `aicmd`, it will prompt you to enter your Google Gemini API key. This key is securely stored in `~/.aicmd.env`. You can obtain a Gemini API key from the [Google AI Studio](https://aistudio.google.com/app/apikey).

## How to Update the Gemini API Key

If you need to change or renew your Gemini API key, use the following command:

```bash
aicmd --renew-key