# black installation

## Windows installation and configuration of black

### reference(s)
* https://black.readthedocs.io/en/stable/integrations/editors.html

### what I did, and how I'd reproduce it

Unless otherwise noted, commands under `File -> Settings` refer to PyCharm. The shortcut to settings is `Ctrl + Alt + S`.

1. create a virtual environment (_e.g._ `just_black`)
2. install requirements from requirements.txt
3. Determine the path to the black executable associated with the above virtual environment (_e.g._ go to interpreter settings, look in the same scripts directory as the python executable associated with that environment for black.exe)
3. go to `File -> Settings -> Tools -> External Tools` and click `+`, entering the following:
* Name: Black
* Description: [whatever]
* Program: path from above step, including "`\black.exe`" at the end
* Arguments: "`$FilePath$`" (with dollar signs and camelcase, without quotes)
4. install **File Watchers** plugin in PyCharm, if it isn't already installed (File -> Settings -> Plugins -> _etc._)
5. in PyCharm, go to `File -> Settings -> Tools -> File Watchers` and click `+` (if it isn't there, check the previous step). Enter the following:
* Name: Black
* File Type: Python
* Scope: Project Files
* Program: path from above step, including "`\black.exe`" at the end
* Arguments: `$FilePath$`
* Output paths to refresh: `$FilePath$`
* Working Directory: `$ProjectFileDir$` (you may need to expand the dropdown)
* Advanced Options: uncheck "Auto Save..." and "Trigger the watcher on external changes" (you may need to expand another dropdown)