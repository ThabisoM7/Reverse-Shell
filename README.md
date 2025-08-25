# Techical Documentation

Learnt how to build a reverse shell, allowing an attacker access to a target system.. I went through the work of Mr. Yosifovich; the author of the book: "Windows Internals" to guide me in building the base and I have debugged and added extra functionality.

---
# Architecture: 
Two applications—local.exe (controller) and remote.exe (target)—communicate over the network. remote.exe executes commands via CMD and relays the output.

<p align="center">
  <img src="https://github.com/ThabisoM7/Reverse-Shell/blob/master/image.png" width="100%" />
</p>

---
A console app in Visual Studio that initializes Winsock 2.
Setting up a listening socket on a chosen port (e.g., 5555), bind, listen, and accept a connection from remote.exe

Another console app that connects back to local.exe.
Builds a TCP client socket, connects to the controller's IP and port.

---
Two pipes with handle inheritance:
One for writing commands to CMD.
One for reading CMD output.
Launch cmd.exe with redirected stdin/stdout using CreateProcess, STARTUPINFO, and flags like CREATE_NO_WINDOW.

Once deployed, the controller can send arbitrary Windows shell commands to the target remotely via CMD, with output returned—useful for remote control and potentially stealthy operations.

When Running Application:
Run Local.exe and Remote.exe both in debug simultaneously.
