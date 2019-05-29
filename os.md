# Shell

## Scripting

- [Make pwd result in terms of “~"](https://unix.stackexchange.com/questions/207210/make-pwd-result-in-terms-of).

### `: "${APPLICATION_PACKAGE_NAME?Required env variable APPLICATION_PACKAGE_NAME}"`

The leading `:` is the built-in [colon command](https://gerardnico.com/lang/bash/double_point), it's used here to expand its arguments. The `${}` is [parameter expansion](https://gerardnico.com/lang/bash/parameter_expansion). The `"` are not needed and the command can be written as `: ${APPLICATION_PACKAGE_NAME?Required env variable APPLICATION_PACKAGE_NAME}`.

If the parameter is not set or is null, the provided error after `?`, i.e `Required env variable APPLICATION_PACKAGE_NAME`, will be displayed. If the shell is not interactive, the script will exit. Otherwise, the value of the parameter is substituted, in this case the substituted value will be considered as a command resulting in `bash: <substituted value>: command not found` error. Having the leading `:` will [prevent](https://aplawrence.com/Basics/leading-colon.html) that error from happening.

### Resources

- [Bash Guide for Beginners](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html).
- [Advanced Bash-Scripting Guide](https://www.tldp.org/LDP/abs/html/index.html).
- [explainshell](https://explainshell.com/).

### Tools

- [shellcheck](https://github.com/koalaman/shellcheck).
