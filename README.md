## Finder-Workspace

A alfred workflow for the Finder that save folder path to the file and restore the window quickly next time.



## Save workspace

First, input the command ***save*** with Alfred and enter.

![](./docs/images/save command.png)

Second, choose the path and input the file name.

![](docs/images/save.png)

Finally, it will generate the applescript file like this:

```applescript
set paths to {"/Users/hzh/test/","/Users/hzh/","/Users/hzh/Downloads/"}
set _length to get the length of paths

tell application "Finder"
    activate
    set _window to make new Finder window
    select _window

    set i to 1
    repeat with _path in paths
        delay 0.1

        set target of front window to (_path as POSIX file)

        if i < _length then
            tell application "System Events"
                tell application process "Finder" to set frontmost to true
                keystroke "t" using command down
            end tell
        end if

        set i to i + 1
    end repeat
end tell
```

> Warnning

It will get all the window path not only current window. So you have to close other window that you want not to save. I tried many methods to no avail because the appscript have no the function which can distinct the window and tab. If you have other great idea, please tell me.



## Open workspace

Input the command ***finder*** with Alfred and enter. It will restore all the window.

![](docs/images/search.png)



## Supported version for Alfred

***>= 4.0.0***



I created it by the Alfred 4. 

The version below 4 may cannot work.



## Download

You can download from [Packal](http://www.packal.org/workflow/finder-workspace) or click [here](https://github.com/hzh-cocong/Finder-Workspace/releases/download/v1.0.0/Finder.Workspace.alfredworkflow)

