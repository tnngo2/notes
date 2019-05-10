# Daemon
A daemon runs as a background process rather than being under the direct control of an interactive user.

Traditionally, a daemon process ends with letter `d`
such as `sshd`

In Unix, a daemon is either
- Created by a process forking a child process, and then immediately exiting, this causing the `init` process to adopt the child process
- directly launching by the init process