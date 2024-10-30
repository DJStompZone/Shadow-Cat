# Shadow-Cat

This project is a Python-based replacement for the traditional `netcat` tool. It provides similar functionalities such as listening for incoming connections, executing commands upon connection, initiating a command shell, and uploading files to a specified destination.

## Features

- **Listening Mode**: Listen on a specified host and port for incoming connections.
- **Command Execution**: Execute a specified command upon receiving a connection.
- **Command Shell**: Initialize a command shell, allowing remote command execution.
- **File Upload**: Upload a file to a specified destination on the target machine upon receiving a connection.

## Usage

```bash
python shadow-cat.py -t target_host -p port [options]
```

## System Wide Install (Optional)
### Installation
You can add shadow-cat to a location on your `PATH` to make it available anywhere
Note: You can `echo $PATH` to view your current `PATH` locations
```bash
# Feel free to change this to whatever/wherever you want
BIN_FILE_NAME="shadcat"
BIN_PATH="/usr/bin/${BIN_FILE_NAME}"

sudo cp shadow-cat.py "$BIN_PATH"
sudo chmod a+x "$BIN_PATH"
```

 ### Usage
 Then, you can execute from anywhere by invoking `shadcat`

## Options
- -h, --help : Show the help message and usage information.
- -l, --listen : Listen on [host]:[port] for incoming connections.
- -e, --execute=file_to_run : Execute the given file upon receiving a connection.
- -c, --command : Initialize a command shell upon receiving a connection.
- -u, --upload=destination : Upon receiving a connection, upload a file and write to the specified [destination].
Examples
Start a command shell on the target:

Copy code
```bash
python shadow-cat.py -t 192.168.0.1 -p 5555 -l -c
```
Upload a file to the target:

Copy code
```bash
python shadow-cat.py -t 192.168.0.1 -p 5555 -l -u=c:\\target.exe
```
Execute a command on the target:

Copy code
```bash
python shadow-cat.py -t 192.168.0.1 -p 5555 -l -e="cat /etc/passwd"
```
Send data to a remote server:

Copy code
```bash
echo 'Hello World' | python shadow-cat.py -t 192.168.11.12 -p 135
```
## How It Works
### Client Mode:

If you provide a target and port without the --listen option, the script will initiate a connection to the target.
It will read data from standard input (stdin) and send it to the target.
The client will then wait for a response from the server and display it.

### Server Mode:

If you use the --listen option, the script will start a server on the specified host and port.
It will accept incoming connections and either execute commands, initiate a shell, or handle file uploads based on the provided options.
Important Notes
Security Warning: This tool is powerful and can be used for both legitimate and malicious purposes. Use it responsibly and only on systems where you have explicit permission to test or work.
Cross-Platform: This script should work on any platform where Python is available, including Linux, macOS, and Windows.

# MIT License

Copyright (c) [2024] [Shadowdrums]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
