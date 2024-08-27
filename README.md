# Microcontroller-Data-Acquisition

This Python script allows you to communicate with serial devices, send commands, receive data, and visualize that data in real-time using Matplotlib. The script is highly flexible and can be used with various devices that communicate over serial ports.

## Features

- **Serial Communication**: Connects to serial devices and sends user-defined commands.
- **Real-Time Data Visualization**: Dynamically plots data received from the device in real-time.
- **Flexible Usage**: Does not require predefined modes, making it adaptable to a wide range of devices and applications.
- **Cross-Platform**: Works on Windows, macOS, and Linux.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Dependencies](#dependencies)
- [Configuration](#configuration)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

## Installation

To get started, clone the repository to your local machine:

```bash
git clone https://github.com/petermetry/Microcontroller-Data-Acquisition.git
cd serial-data-visualization

## Dependencies

Ensure you have Python 3 installed. You can install the required Python packages using pip:

```bash
pip install -r requirements.txt

If the requirements.txt file is not provided, manually install the dependencies:

```bash
pip install pyserial matplotlib


## Usage

- [Connect your device to a serial port on your computer.]

- [Run the script:]

```bash
python serial_visualization.py

- [Select the COM port when prompted.]

- [Enter commands in the terminal as needed.]

- [View real-time plots of the data returned by your device.]

## Configuration

- [###Serial Configuration: By default, the script uses a baud rate of 9600 and a timeout of 1 second. These can be modified in the configure_serial function within the script.]
- [###Data Format: The script expects the serial device to return data in key-value pairs (e.g., Time: 10, RPM: 100, Angle: 30). This format can be adjusted by modifying the collect_data function.]
