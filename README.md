# Microcontroller-Data-Acquisition

This Python script allows you to communicate with serial devices, send commands, receive data, and visualize that data in real-time using Matplotlib. The script is highly flexible and can be used with various devices that communicate over serial ports.

## Features

- **Serial Communication**: Connects to serial devices and sends user-defined commands.
- **Real-Time Data Visualization**: Dynamically plots data received from the device in real-time.
- **Flexible Usage**: Does not require predefined modes, making it adaptable to a wide range of devices and applications.
- **Cross-Platform**: Works on Windows, macOS, and Linux.

## Table of Contents

- [Installation](#installation)
- [Dependencies](#dependencies)
- [Usage](#usage)
- [Configuration](#configuration)
- [Examples](#examples)
- [Contributing](#contributing)

## Installation

To get started, clone the repository to your local machine:

```bash
git clone https://github.com/petermetry/Microcontroller-Data-Acquisition.git
cd Microcontroller-Data-Acquisition
```

## Dependencies

This project requires the following dependencies:

- **Python 3**: Ensure that Python 3 is installed on your system. You can download it from the [official Python website](https://www.python.org/).

- **PySerial**: A library used for serial communication with devices. You can install it by running:
  ```bash
  pip install pyserial
  ```
- **Matplotlib**: A plotting library used for real-time data visualization. Install it with:
```bash
pip install matplotlib
```

## Usage

- **Connect your device to a serial port on your computer.**

- **Run the script:**

```bash
python serial_visualization.py
```
- **Select the COM port when prompted.**

- **Enter commands in the terminal as needed.**

- **View real-time plots of the data returned by your device.**

## Examples

### Sending Commands

You can send any command to your device directly through the terminal:

```bash
Enter a command to send to the device (or type 'exit' to quit): 12345
Sending command: 12345
Received response:
Time: 10, RPM: 100, Angle: 30
```

### Real-Time Plotting
Data received from the device is automatically plotted in real-time. The plot updates dynamically as new data arrives.


## Contributing
Contributions are welcomed! If you have suggestions, improvements, or new features to add, feel free to open a pull request or submit an issue.

### How to Contribute
- **Fork the repository.**
- **Create a new branch (git checkout -b feature-branch).**
- **Make your changes and commit them (git commit -am 'Add new feature').**
- **Push to the branch (git push origin feature-branch).**
- **Open a pull request.**
