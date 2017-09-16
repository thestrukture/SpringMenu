# ⚜️ Spring menu.

JS plugins to interact with selected code. Spring menu plugins operate on the front end (via JS) and on the backend via Go code.

## How it works?
Each plugin is a repository. Each repository has an `index.js`. The contents of this file will be ran on web page load.

### Register plugin
Within your `index.js` invoke the function `$trukture.addPlugin(plugin)`. Refer to the function list below to view the properties  of a `plugin`.

### Access to shell
Prior to execution of your plugin, the working directory will be changed to the package of the resource you are using. Invoke `$trukture.exec(cmd, callback)` to access your user's shell directly.

### $trukture function list :

#### `plugin` properties.
Object sample:

	{
     	name: "spring me",
     	show : function(code){return true;},
     	exec : function(code){ return false; }
     }

Property descriptions :

- name : Name of plugin within  menu.
- show : function ran to determine if selected line is applicable to plugin. vars :: code  - selected line.
- exec : function ran if option is chosen within menu. vars :: code - selected line. To replace the selected line return a string, otherwise `return false`. 

### $trukture.addPlugin(plugin)
Add a new plugin to spring menu. Invoked from within `index.js`

### $trukture.exec(cmd, callback)
Run a command within your user's shell. vars:: cmd - string command to run in shell, callback - function called on command completion. This function has two variables `response` and `log`.  On error response will return `false` and log will contain information about command failure.

Example

	
     		 	$trukture.exec("go build",function(success, log){
     		 		if (!success ) {
     		 			alert("Error running commmand! " + log)
     		 		}
     		 	})

## How to display HTML?
Use the css selector `.side-bay` to access a user visible alert box.

## How to add plugins?
Within the Strukture click on the `plugins` button to open your plugin manager.

## How to build a new plugin?

Download this [repository](https://github.com/thestrukture/GoGet) to get a smooth started.
