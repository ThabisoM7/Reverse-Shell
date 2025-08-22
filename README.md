# Techinal Documentation

Learnt to build a reverse shell, allowing an attacker access to a target system.

---
# Overview of architecture: 
Two applications—local.exe (controller) and remote.exe (target)—communicate over the network. remote.exe executes commands via CMD and relays the output.

---
Create a console app in Visual Studio that initializes Winsock 2.
Set up a listening socket on a chosen port (e.g., 5555), bind, listen, and accept a connection from remote.exe.

Another console app that connects back to local.exe.
Builds a TCP client socket, connects to the controller's IP and port.

---
Set up two anonymous pipes with handle inheritance:
One for writing commands to CMD.
One for reading CMD output.
Launch cmd.exe with redirected stdin/stdout using CreateProcess, STARTUPINFO, and flags like CREATE_NO_WINDOW.

Once deployed, the controller can send arbitrary Windows shell commands to the target remotely via CMD, with output returned—useful for remote control and potentially stealthy operations.
