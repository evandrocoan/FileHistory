# SublimeText - File History #

**Sublime Text 2 and 3** plugin
to provide access to the history of recently used files -
project-wise or globally.

The most recently closed file
can be instantly re-opened
or the entire file history
can be shown and filtered in a quick panel
(including file preview
and the ability to open multiple files).

![Preview Image][preview-img]


## Features ##

* Reopen the most recently closed file
  or open a quick panel of recently used files
  to choose from
* Display a preview of the file
  while browsing the quick panel
  (only Sublime Text 3)
* Open multiple history entries
  from the quick panel
  with the <kbd>Right</kbd> key
* Delete history entries from the quick panel
  with <kbd>Ctrl + Del</kbd>
* Optionally remove any non-existent files
  while looking through the file history
  (when previewed or opened)
  or on start-up
* Creates backups
  in case you lose your history
* Highly configurable through [FileHistory.sublime-settings][] file,
  like excluding files with regex patterns


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
   wait few seconds until the installation finishes up
1. Now,
   Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Go to the menu **`Tools -> Command Palette...
   (Ctrl+Shift+P)`**
1. Type **`Preferences:
   Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   find the following setting on your **`Package Control.sublime-settings`** file:
   ```js
       "channels":
       [
           "https://packagecontrol.io/channel_v3.json",
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
       ],
   ```
1. And,
   change it to the following, i.e.,
   put the **`https://raw.githubusercontent...`** line as first:
   ```js
       "channels":
       [
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
           "https://packagecontrol.io/channel_v3.json",
       ],
   ```
   * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
     you will not install this forked version of the package,
     but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
   go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
search for **`FileHistory`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## Usage ##

To use the plugin,
open the Command Palette
and search for `File History:`.

When you opened a panel
you can use the <kbd>Right</kbd> key
to open the file and keep the panel open,
or <kbd>Ctrl/Cmd + Del</kbd>
to remove the selected file from the history.

For default keymap definitions,
see [Default (Windows).sublime-keymap][keymap] ([OSX][keymap-osx]).

For the available and default settings,
see [FileHistory.sublime-settings][].

### Project Settings ###

You can **extend**
the `path_exclude_patterns` and `path_reinclude_patterns` lists
in your project settings.

For this,
add a `"file_history"` dictionary
to your project's settings
and then one or both of the settings to that.
Example:

```json
{
    "folders": [
        {
            "path": "."
        }
    ],
    "settings": {
        "file_history": {
            "path_exclude_patterns": ["/bin/"],
            "path_reinclude_patterns": ["\\.compiled$"]
        }
    }
}
```

### Commands ###

**open_recently_closed_file** (Window)

Opens a popup with recently closed files
or reopens the lastly closed view
if `action == "open_latest_closed"`.

> *Parameters*
>
> - **action** (str) -
>   *Default*: `"show_history"`,
>   *Allowed values*: `"show_history"`, `"open_latest_closed"`
>
> - **current_project_only** (bool) -
>   *Default*: `True`

**cleanup_file_history** (Window)

Checks the current project
or the whole history
for non-existent files
and removes them from the history.

>   *Parameters*
>
>   - **current_project_only** (bool) -
>     *Default*: `True`

**reset_file_history** (Window)

Removes all history data.


[github]: https://github.com/FichteFoll/sublimetext-filehistory "Github.com: FichteFoll/sublime-filehistory"
[pck-ctrl]: http://wbond.net/sublime_packages/package_control "Sublime Package Control by wbond"

[FileHistory.sublime-settings]: FileHistory.sublime-settings

[keymap]: Default%20%28Windows%29.sublime-keymap "Default.sublime-keymap"
[keymap-osx]: Default%20%28OSX%29.sublime-keymap "Default (OSX).sublime-keymap"

[preview-img]: https://cloud.githubusercontent.com/assets/931051/14301433/2178c37c-fb98-11e5-8f70-f2e032d3479f.gif
