# Misc

- https://github.com/nodejs/node-gyp/blob/master/macOS_Catalina.md
- https://apple.stackexchange.com/questions/136672/how-do-i-require-password-prompt-every-time-i-close-my-macbooks-lid
- https://support.apple.com/lt-lt/guide/mac-help/mchlp2322/mac
- [avoid moving desktop to another position](https://osxdaily.com/2011/11/12/stop-spaces-rearranging-mac-os-x/)
- https://filipmolcik.com/macbook-wifi-issue-os-x-keeps-reconnecting/
- [Is Apple silicon ready](https://isapplesiliconready.com/)
- https://mattbanderson.com/so-you-hosed-your-mac-os-python-install/ (python, python3)
- [Homebrew and Git - Wrong language on the command line](https://apple.stackexchange.com/questions/337244/homebrew-and-git-wrong-language-on-the-command-line)

# Printing

- [Mac: How to change default printer settings](https://support.pirateship.com/en/articles/2799085-mac-how-to-change-default-printer-settings)
- [Here Are Two Ways To Print Multiple Files At Once In MacOS](https://www.alphr.com/print-multiple-files-mac/)


# Apps

- Productivity: https://www.alfredapp.com/ VS https://raycast.com/
- https://contexts.co/
- https://gpgtools.org/
- https://awaremac.com/
- https://muzzleapp.com/
- https://highlyopinionated.co/swish/
- https://github.com/leits/MeetingBar
- [API tool/HTTP client](https://paw.cloud/)


# Commands

- https://osxdaily.com/2010/08/22/install-watch-command-on-os-x/

# Store env variables in keychain

Storing a secret in an env variable to be used in the terminal is something so common, the problem is that you don't want to harcode it in your `.zshrc` file for security reasons. The solution is to [store it in the keychain](https://medium.com/@johnjjung/how-to-store-sensitive-environment-variables-on-macos-76bd5ba464f6) (you have to use `export`, which is missing in the linked article, when you define the env variable).

The second problem is that `.zshrc` file is a file that you're bookmarking in case you will need it one day when e.g you change your machine. Having inside it content related to reading env variables from the keychain is unrelevant. The solution is to [use the `.zshenv` file instead which is dedicated to env variables](http://zsh.sourceforge.net/Intro/intro_3.html).

In a nutshell, when you have an important secret, you first store it in a cloud vault, e.g Dashlane, you then store it in the macos keychain if you will use it in the terminal. The reason why you need to store it in both vaults is the keychain vault being a local one, once you reset your account, you lost all the secrets stored into it. Lastly, you export the env variable in the `.zshenv` file by using the `security` CLI to retrieve the env variable from the keychain.
