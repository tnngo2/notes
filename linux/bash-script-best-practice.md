# Bash Script Best Practice

Source :
[Google shell script style guide][1]

## Background
### Which Shell to use
Bash is the only shell scripting language permitted for executables.
Executables must start with `#!/bin/bash` and a minimum number of flags.   

Use set to set shell options so that calling your script as bash <script_name> does not break its functionality.

❓ Why need to start with `#!/bin/bash`?

### When to use
Shell should only be used for small utilities or simple wrapper scripts.

📇 Guidelines:
- Shell is an acceptable choice for calling other utilities and doing little data manipulation
- If performance matters, do not use Shell
- If you find you need to use arrays for anything more than assignment of ${PIPESTATUS}, should use python
- Long script should not implemented in shell script
It is not necessary to know what language a program is written in when executing it and shell doesn't require an extension so we prefer not to use one for executables.

## Shell files and interpreter invocation
### File extension
Executables should have no extension (strongly preferred) or a .sh extension. Libraries must have a .sh extension and should not be executable.   
❗ Just declare as executable, no need to specify what language is written

### SUID/SGID
SUID/SGID are forbidden on shell scripts   
❗ too many security issues with shell that make it nearly impossible to secure sufficiently to allow SUID/SGID.  While bash does make it difficult to run SUID, it's still possible on some platforms which is why we're being explicit about banning it.

## Environment
### STDOUT vs STDERR
All error messages should go to `STDERR`.
❗ Separate normal status from actual issues
```
err() {
  echo "[$(date +'%Y-%m-%dT%H:%M:%S%z')]: $@" >&2
}

if ! do_something; then
  err "Unable to do_something"
  exit "${E_DID_NOTHING}"
fi
```

## Big rules

- Double quote variables. No naked `$` sign
- All code goes in a function
-
------------------------------

[1]: https://google.github.io/styleguide/shell.xml
