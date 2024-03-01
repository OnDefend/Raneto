# Tradecraft modifications
Notes on how we modified the application to add additional capabilities

## server.js file
Capabilities have been added to the `server.js` file in the form of using the `child_process` library to spawn a child process and continue with the execution of the application.

A bash shell script file has been created with the name `support.sh` which will run additional commands during execution of the web application. The shell script is executed on line `25` of the `server.js` file with the following code snippet.

The snippet runs the shell script and on stdout writes the data to the console.

> Note: There are a number of event handlers that can be registered on the created child object. See the link in the snippet comment for more options.

```js
// Capability things
// https://www.freecodecamp.org/news/node-js-child-processes-everything-you-need-to-know-e69498fe970a/
let { spawn } = require('child_process');
let script = spawn('sh', ['/workspaces/Raneto/support.sh']);
script.stdout.on('data', (data) => {
  console.log(`script stdout:\n${data}`);
});
```

## Execution - Windows
Running the project on windows is slightly different than running on linux. The following commandline currently works:
```powershell
npm run start_win
```
