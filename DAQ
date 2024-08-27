# Author: Peter Metry
# This script is designed to interface with a serial device, sending commands and receiving data, which is then visualized using matplotlib.
# Contact: metryp@uni.coventry.ac.uk

import serial
import serial.tools.list_ports
import time
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

def list_ports():
    """Lists all available COM ports."""
    ports = serial.tools.list_ports.comports()
    if not ports:
        print("No COM ports found. Please check your connections.")
    else:
        for port in ports:
            print(f"{port.device} - {port.description}")
    return [port.device for port in ports]

def select_com_port():
    """Prompts the user to select a COM port from available options."""
    ports = list_ports()
    if not ports:
        return None
    for idx, port in enumerate(ports):
        print(f"{idx + 1}: {port}")
    try:
        selection = int(input("Select COM Port by number: ")) - 1
        if 0 <= selection < len(ports):
            selected_port = ports[selection]
            print(f"Selected port: {selected_port}")
            return selected_port
        else:
            print("Invalid selection. Please try again.")
            return select_com_port()
    except ValueError:
        print("Invalid input. Please enter a number.")
        return select_com_port()

def configure_serial(port, baudrate=9600, timeout=1):
    """Configures and opens a serial port."""
    serialInst = serial.Serial()
    serialInst.baudrate = baudrate
    serialInst.port = port
    serialInst.timeout = timeout
    try:
        serialInst.open()
    except serial.SerialException as e:
        print(f"Failed to open serial port: {e}")
        return None
    return serialInst

def send_command(serialInst, command):
    """Sends a command over the serial connection."""
    if isinstance(command, int):
        command = str(command)
    try:
        print(f"Sending command: {command}")
        serialInst.write(command.encode('utf-8'))
        serialInst.write(b'\n')
        time.sleep(0.5)
    except serial.SerialException as e:
        print(f"Failed to send command: {e}")

def read_response(serialInst):
    """Reads the response from the serial device."""
    response = []
    try:
        while serialInst.in_waiting:
            line = serialInst.readline().decode('utf-8').strip()
            response.append(line)
        if response:
            print("Received response:")
            for line in response:
                print(line)
    except serial.SerialException as e:
        print(f"Failed to read response: {e}")
    return response

def clear_serial_buffer(serialInst):
    """Clears the serial input buffer."""
    try:
        serialInst.reset_input_buffer()
    except serial.SerialException as e:
        print(f"Failed to clear serial buffer: {e}")

def collect_data(serialInst, data_storage):
    """Collects data from the serial response and stores it in a dictionary."""
    response = read_response(serialInst)
    for line in response:
        print(f"Debug: Raw Line: {line}")  # Debugging output
        try:
            # Assuming the data is in key:value pairs separated by commas
            parts = line.split(',')
            for part in parts:
                key, value = part.split(':')
                key = key.strip()
                value = float(value.strip())
                if key not in data_storage:
                    data_storage[key] = []
                data_storage[key].append(value)
            print(f"Collected data: {data_storage}")
        except (ValueError, IndexError) as e:
            print(f"Error parsing line: {line} - {e}")

def update_plot(frame, serialInst, data_storage, ax):
    """Updates the plot dynamically based on the collected data."""
    collect_data(serialInst, data_storage)
    
    # Clear previous plot
    ax.clear()
    
    # Plot each data set
    for key, values in data_storage.items():
        ax.plot(values, label=key)
    
    ax.set_title('Real-time Data Visualization')
    ax.legend()
    ax.grid(True)
    ax.relim()  
    ax.autoscale_view()  

def main_loop():
    """Main loop for selecting the COM port, sending commands, and visualizing data."""
    port = select_com_port()
    if not port:
        return

    serialInst = configure_serial(port)
    if not serialInst:
        return

    data_storage = {}  # Dictionary to store different data streams

    fig, ax = plt.subplots()
    ani = FuncAnimation(fig, update_plot, fargs=(serialInst, data_storage, ax), interval=1000, cache_frame_data=False)

    while True:
        command = input("Enter a command to send to the device (or type 'exit' to quit): ")

        if command.lower() == 'exit':
            break

        clear_serial_buffer(serialInst)
        send_command(serialInst, command)
        read_response(serialInst)

    serialInst.close()
    plt.show()

if __name__ == "__main__":
    main_loop()
