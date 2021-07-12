# Misc

- Select next occurance keyboard shortcut: cmd + d
- [Sync settings, extensions, etc.](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)
- [Performance issues and how to troubleshoot them](https://github.com/Microsoft/vscode/wiki/Performance-Issues)
- debug extension: follow the answer [here](https://stackoverflow.com/questions/51164279/how-to-debug-visual-studio-code-extensions) except that instead of opening the installed extension, get its code from github and open it in vscode, you will then will find the debug configurations ready to use.
- [native tabs](https://worthdoingbadly.com/vscodetabs/)
- [Visual Studio Code tips and tricks](https://channel9.msdn.com/Events/Build/2020/BOD103?ocid=AID3012654&WT.mc_id=build2020-azuredevtips-micrum)
- ["electron_node server.js" high cpu usage](https://github.com/microsoft/vscode/issues/88854)

# Automatic Type Acquisition

This is a very powerful feature, I followed the [guidelines](https://code.visualstudio.com/docs/nodejs/working-with-javascript#_typings-and-automatic-type-acquisition) but without any luck. I had the following `tsconfig.json` config.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "checkJs": true,
    "esModuleInterop": true
  },
  "include": [
    "./packages-application",
    "./packages-shared",
    "node_modules/cypress",
    "cypress"
  ]
}
```

and the file that I was interested in was in `packages-shared` folder. I was importing `faker` and the intellisense wasn't working as it's supposed to be, I made sure that `@types/faker` was already aquired by vscode by checking the log, it's a file named `ti-*.log` in the same folder where the typescript server log file is located. This latter can be open by using the command `TypeScript: Open TS server log`.

I then discoverd that if I remove `./packages-shared` entry from the config file the intellisense will start working. But in this case typescript checking will stop working for the files in that folder, which I don't want to happen.

I then tried to use `jsconfig.json` file instead, and the intellisense was working without deleting `./packages-shared`.

After checking the typescript server log, when using both `tsconfig.json` and `jsconfig.json` and comparing the results, I noticed that `typeAcquisition.enable` config was set to `true` in `jsconfig.json` file, and to `false` in `tsconfig.json` file. After adding it to the latter, the problem was solved.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "checkJs": true,
    "esModuleInterop": true
  },
  "include": [
    "./packages-application",
    "./packages-shared",
    "node_modules/cypress",
    "cypress"
  ],
  "typeAcquisition": {
    "enable": true
  }
}
```

# macos vscode code helper cpu 100

The problem is caused by code helper.

TODO:

- [ ] After inspecting processes as described [here](https://github.com/Microsoft/vscode/wiki/Performance-Issues), `electron_node tsserver` extension has a high usage of cpu, disable it and test

# Resources

- [vscode can do that](https://vscodecandothat.com/)
- [microsoft/vscode-recipes](https://github.com/microsoft/vscode-recipes)
