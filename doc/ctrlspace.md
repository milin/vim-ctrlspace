*ctrlspace.txt*             For Vim version 7.3+      Last change: 2015.09.16
*ctrlspace*
*vim-ctrlspace*






                           Vim-CtrlSpace 5.0.6~

                           Vim Space Controller






Copyright (c) 2013-2015 Szymon Wrozynski and Contributors

==========================================================================

Table of Contents                                            *ctrlspace-toc*

 1. Overview                                            |ctrlspace-overview|
   1.1 Version 5                                       |ctrlspace-version-5|
 2. Idea by Analogy                                         |ctrlspace-idea|
 3. Getting Started                              |ctrlspace-getting-started|
   3.1 Installation                                 |ctrlspace-installation|
   3.2 Basic Settings                             |ctrlspace-basic-settings|
     3.2.1 Go Engine                                   |ctrlspace-go-engine|
     3.2.2 Symbols                                       |ctrlspace-symbols|
     3.2.3 Glob Command                             |ctrlspace-glob-command|
     3.2.4 Search Timing                           |ctrlspace-search-timing|
     3.2.5 Colors                                         |ctrlspace-colors|
   3.3 First Steps                                   |ctrlspace-first-steps|
 4. User Interface                                            |ctrlspace-ui|
   4.1 Status Line                                   |ctrlspace-status-line|
   4.2 Tabline                                           |ctrlspace-tabline|
   4.3 Project Root                                 |ctrlspace-project-root|
 5. Lists                                                  |ctrlspace-lists|
   5.1 Buffer List                                   |ctrlspace-buffer-list|
     5.1.1 Single Mode                               |ctrlspace-single-mode|
     5.1.2 Visible Mode                             |ctrlspace-visible-mode|
     5.1.3 All Mode                                     |ctrlspace-all-mode|
   5.2 File List                                       |ctrlspace-file-list|
   5.3 Tab List                                         |ctrlspace-tab-list|
   5.4 Workspace List                             |ctrlspace-workspace-list|
   5.5 Bookmark List                               |ctrlspace-bookmark-list|
 6. Common Modes                                    |ctrlspace-common-modes|
   6.1 Zoom Mode                                       |ctrlspace-zoom-mode|
   6.2 Next Tab Mode                               |ctrlspace-next-tab-mode|
   6.3 Search Mode                                   |ctrlspace-search-mode|
   6.4 Nop Mode                                         |ctrlspace-nop-mode|
   6.5 Help Mode                                       |ctrlspace-help-mode|
 7. Configuration                                  |ctrlspace-configuration|
   7.1 g:CtrlSpaceHeight                                 |g:CtrlSpaceHeight|
   7.2 g:CtrlSpaceMaxHeight                           |g:CtrlSpaceMaxHeight|
   7.3 g:CtrlSpaceSetDefaultMapping           |g:CtrlSpaceSetDefaultMapping|
   7.4 g:CtrlSpaceDefaultMappingKey           |g:CtrlSpaceDefaultMappingKey|
   7.5 g:CtrlSpaceKeys                                     |g:CtrlSpaceKeys|
   7.6 g:CtrlSpaceHelp                                     |g:CtrlSpaceHelp|
   7.7 g:CtrlSpaceGlobCommand                       |g:CtrlSpaceGlobCommand|
   7.8 g:CtrlSpaceUseTabline                         |g:CtrlSpaceUseTabline|
   7.9 g:CtrlSpaceUseMouseAndArrowsInTerm
                                        |g:CtrlSpaceUseMouseAndArrowsInTerm|
   7.10 g:CtrlSpaceSaveWorkspaceOnExit      |g:CtrlSpaceSaveWorkspaceOnExit|
   7.11 g:CtrlSpaceSaveWorkspaceOnSwitch  |g:CtrlSpaceSaveWorkspaceOnSwitch|
   7.12 g:CtrlSpaceLoadLastWorkspaceOnStart
                                       |g:CtrlSpaceLoadLastWorkspaceOnStart|
   7.13 g:CtrlSpaceCacheDir                            |g:CtrlSpaceCacheDir|
   7.14 g:CtrlSpaceProjectRootMarkers        |g:CtrlSpaceProjectRootMarkers|
   7.15 g:CtrlSpaceUseUnicode                        |g:CtrlSpaceUseUnicode|
   7.16 g:CtrlSpaceSymbols                              |g:CtrlSpaceSymbols|
   7.17 g:CtrlSpaceIgnoredFiles                    |g:CtrlSpaceIgnoredFiles|
   7.18 g:CtrlSpaceStatuslineFunction        |g:CtrlSpaceStatuslineFunction|
   7.19 g:CtrlSpaceSearchTiming                    |g:CtrlSpaceSearchTiming|
   7.20 g:CtrlSpaceFileEngine                        |g:CtrlSpaceFileEngine|
 8. API                                                      |ctrlspace-api|
   8.1 Commands                                         |ctrlspace-commands|
     8.1.1 :CtrlSpace [keys]                                    |:CtrlSpace|
     8.1.2 :CtrlSpaceGoUp                                   |:CtrlSpaceGoUp|
     8.1.3 :CtrlSpaceGoDown                               |:CtrlSpaceGoDown|
     8.1.4 :CtrlSpaceTabLabel                           |:CtrlSpaceTabLabel|
     8.1.5 :CtrlSpaceClearTabLabel                 |:CtrlSpaceClearTabLabel|
     8.1.6 :CtrlSpaceSaveWorkspace [workspace]     |:CtrlSpaceSaveWorkspace|
     8.1.7 :CtrlSpaceNewWorkspace                   |:CtrlSpaceNewWorkspace|
     8.1.8 :CtrlSpaceLoadWorkspace [!] [workspace] |:CtrlSpaceLoadWorkspace|
     8.1.9 :CtrlSpaceAddProjectRoot [dir]         |:CtrlSpaceAddProjectRoot|
     8.1.10 :CtrlSpaceRemoveProjectRoot [dir]  |:CtrlSpaceRemoveProjectRoot|
   8.2 Functions                                       |ctrlspace-functions|
     8.2.1 ctrlspace#api#BufferList({tabnr})    |ctrlspace#api#BufferList()|
     8.2.2 ctrlspace#api#Buffers({tabnr})          |ctrlspace#api#Buffers()|
     8.2.3 ctrlspace#api#TabModified({tabnr})  |ctrlspace#api#TabModified()|
     8.2.4 ctrlspace#api#Statusline()           |ctrlspace#api#Statusline()|
     8.2.5 ctrlspace#api#StatuslineTabSegment()
                                      |ctrlspace#api#StatuslineTabSegment()|
     8.2.6 ctrlspace#api#StatuslineModeSegment({...})
                                     |ctrlspace#api#StatuslineModeSegment()|
     8.2.7 ctrlspace#api#TabBuffersNumber({tabnr})
                                          |ctrlspace#api#TabBuffersNumber()|
     8.2.8 ctrlspace#api#TabTitle({tabnr}, {bufnr}, {bufname})
                                                  |ctrlspace#api#TabTitle()|
     8.2.9 ctrlspace#api#Guitablabel()         |ctrlspace#api#Guitablabel()|
     8.2.10 ctrlspace#api#Tabline()                |ctrlspace#api#Tabline()|
     8.2.11 ctrlspace#api#BufNr()                    |ctrlspace#api#BufNr()|
 9. File Engine Specifications                      |ctrlspace-engine-specs|
10. Authors and License                      |ctrlspace-authors-and-license|

==========================================================================

1. Overview                                             *ctrlspace-overview*

Welcome to Vim-CtrlSpace, a comprehensive solution for your Vim editor
providing:

 * tabs / buffers / files management
 * fast fuzzy searching powered by Go
 * workspaces (sessions)
 * bookmarks for your favorite projects

The plugin name follows the convention of naming fuzzy search plugins
after their default mappings (like Command-T or CtrlP), hence the plugin
mapping is by default `Ctrl` + `Space`.

If you like the plugin please don't forget to leave a star for this
project! This will help me to estimate the plugin popularity and plan
further development :).

If you have already starred this repo, thank you! Thanks to you it's my
pet project now :). If you have a question, a feature request, or a new
idea, don't hesitate to post new issues or pull requests. Collaboration
is the most awesome thing in the open source community!

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

1.1 Version 5                                          *ctrlspace-version-5*

Vim-CtrlSpace started over 2 years ago as a fork of another plugin and the
Version 5 is the result of the experience gained during that period and
cooperation with the community.

Version 5 is the biggest upgrade in the plugin history. All plugin code
has been rewritten from scratch taking user feedback as a great resource
of ideas and challenges into account. Thanks to users the plugin has
configurable key mappings and allows you to handle projects with 100 000
files!

In case you're curious, Vim-CtrlSpace 5 took me 5 months of spare evenings
to complete :).

The most exciting features of Vim-CtrlSpace 5 are:

 * better, modular, and extensible code base
 * simplified, well thought-out, and clear design
 * new fuzzy search engine for files (written in Go)
 * more effective and responsive behavior
 * fine-grained configuration

Version 5 is not backward compatible. All configuration variables and API
functions have been renamed. Please check |ctrlspace-configuration| for
more info.

                                                             |ctrlspace-toc|
==========================================================================

2. Idea by Analogy                                          *ctrlspace-idea*

Vim-CtrlSpace interface is a window you can invoke by pressing <C-Space>.
The window displays a list of items. You can select those items with <h>,
<j>, and <CR> keys.

Generally speaking Vim-CtrlSpace can display 5 types of lists:

 * Buffer List
 * File List
 * Tab List
 * Workspace List
 * Bookmark List

Lists can be explained with a simple analogy. Let's imagine Vim is a
writing desk. Your projects are like drawers. The Bookmark List simply
displays your favorite projects.

To get documents from a drawer you would need a File List. It allows you
to easily look up contents of a given project. Once you locate and pick up
a file it becomes a buffer.

A buffer is like a sheet of paper lying on the desk. Sometimes you can
have a blank piece of paper – that's a new unsaved buffer. It would become
eventually a file on the disk once saved (put into a drawer). To manage
all buffers on the desk you would need a Buffer List.

So far our analogy is fairly simple. This workflow is straightforward but
inefficient in the long run with a large amount of files. How could we
optimize it?

The answer are tabs – a secret weapon of Vim-CtrlSpace. Each tab holds a
separate list of buffers. And this is something very different when
compared to plain Vim. Tabs powered by the plugin can be seen as piles of
documents on the desk.

With tabs you can, for example:

 * group related buffers
 * extract to other tabs
 * name them accordingly
 * move or copy them

Tabs usage in Vim-CtrlSpace is quite more extensive than in Vim. This is
because they serve mainly as independent buffer lists, so you are likely
to have plenty of them. Tabs can be accessed and managed within Tab List.

All your buffers, tabs, and tab layouts can be persisted as a workspace.
It's like taking a picture of your desk with an instant camera. You can
save multiple workspaces per project with Workspace List.

                                                             |ctrlspace-toc|
==========================================================================

3. Getting Started                               *ctrlspace-getting-started*

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.1 Installation                                    *ctrlspace-installation*

If you use Vundle add to your `.vimrc`: >

    Plugin 'szw/vim-ctrlspace'
<
You can also clone the repository to your `.vim` directory: >

    cd ~/.vim
    git clone https://github.com/szw/vim-ctrlspace.git .
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.2 Basic Settings                                *ctrlspace-basic-settings*

First please make sure that you set `nocompatible` and `hidden` options
(required by the plugin) in your `.vimrc`: >

    set nocompatible
    set hidden
<
If you feel brave enough turn off tabline: >

    set showtabline=0
<
Tabline in Vim has very limited capabilities and as Vim-CtrlSpace makes
use of tabs intensively, tabline would just get in your way. Tab List
(<l>) makes tabline obsolete ;).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.2.1 Go Engine                                        *ctrlspace-go-engine*

The plugin provides engine compiled for popular operating systems and
architectures. By default it will attempt to detect your os and
architecture. To see if auto detection was successful press <?>.

To find more about file engines check |g:CtrlSpaceFileEngine|.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.2.2 Symbols                                            *ctrlspace-symbols*

Vim-Ctrlspace displays icons in the UI if your font supports UTF8, or
ASCII characters as a fallback. Some symbols (glyphs) might not look well
with the font you are using, so feel free to change and adjust them.

This is the config I use for Inconsolata font in MacVim: >

    if has("gui_running")
        " Settings for MacVim and Inconsolata font
        let g:CtrlSpaceSymbols = { "File": "◯", "CTab": "▣", "Tabs": "▢" }
    endif
<
Since it's impossible to provide universal character set that would look
well on any machine, therefore the fine tuning is left up to you.

You can find more about this tuning option in the plugin help:
|g:CtrlSpaceSymbols|.

If you feel that you have found a better symbol for a given view, you are
more than welcome to open a pull request.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.2.3 Glob Command                                  *ctrlspace-glob-command*

Another important setting is the Glob command (|g:CtrlSpaceGlobCommand|).
This command is used to collect all files in your project directory.
Specifically, I recommend that you install and use `ag`, as it respects
`.gitignore` rules and is really fast. Once it's installed you can add
this line to your `.vimrc`: >

    if executable("ag")
        let g:CtrlSpaceGlobCommand = 'ag -l --nocolor -g ""'
    endif
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.2.4 Search Timing                                *ctrlspace-search-timing*

If you usually have to deal with huge projects having 100 000 files you
can increase plugin fuzzy search delay to make it even more responsible by
providing a higher |g:CtrlSpaceSearchTiming| value: >

    let g:CtrlSpaceSearchTiming = 500
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.2.5 Colors                                              *ctrlspace-colors*

Finally, you can adjust some plugin colors. By default plugin uses
the following setup: >

    hi link CtrlSpaceNormal   PMenu
    hi link CtrlSpaceSelected PMenuSel
    hi link CtrlSpaceSearch   Search
    hi link CtrlSpaceStatus   StatusLine
<
However some color schemes show search results with the same colors as
PMenu groups. If that's your case try to link CtrlSpaceSearch highlight
group to IncSearch instead: >

    hi link CtrlSpaceSearch IncSearch
<
Of course nothing prevents you from providing your own highlighting, for
example: >

    hi CtrlSpaceSearch guifg=#cb4b16 guibg=NONE gui=bold
                     \ ctermfg=9 ctermbg=NONE term=bold cterm=bold
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

3.3 First Steps                                      *ctrlspace-first-steps*

Alright! You've hopefully installed, configured Vim-CtrlSpace, and
restarted Vim (otherwise do it!). Now you're wondering how to start using
this thing.

First, you need to select a project. Vim operates in a directory,
described as `CWD` (Current Working Directory). If you've just started a
MacVim it's probably pointing to your home directory (issue |:pwd| to
check it).

I advise you to add a project to the Bookmark List by opening the plugin
window (<C-Space>) and pressing <b>. The plugin will ask for a project
directory.

Make sure that the path is not home directory. Otherwise the plugin will
start indexing all your files which will be pointless and resource
exhaustive. Be concrete and provide a real path to a project. Once your
bookmark is created, you can go there with <CR>.

Now open some files with <o>. Finally save a workspace with <w> by
providing your first workspace name.

For key reference press <?> inside the plugin window.

                                                             |ctrlspace-toc|
==========================================================================

4. User Interface                                             *ctrlspace-ui*

Vim-CtrlSpace contains 5 different lists: Buffer List, File List, Tab
List, Workspace List, and Bookmark List. Some of those have additional
modes. However, in a modal editor like Vim this should not fear you ;).

You can jump between lists easily by pressing one of the following keys:

| Key | Action                                                |
| --- | ----------------------------------------------------- |
| `h`   | Toggle Buffer List (aka `H`ome List)                    |
| `H`   | Jump to Buffer List (aka `H`ome List) with Search Mode  |
| `o`   | Toggle File List (aka `O`pen List)                      |
| `O`   | Jump to File List (aka `O`pen List) with Search Mode    |
| `l`   | Toggle Tab List (aka `L`ists List)                      |
| `L`   | Jump to Tab List (aka `L`ists List) with Search Mode    |
| `w`   | Toggle `W`orkspace List                                 |
| `W`   | Jump to `W`orkspace List with Search Mode               |
| `b`   | Toggle `B`ookmark List                                  |
| `B`   | Jump to `B`ookmark List with Search Mode                |

Anytime you can return by pressing <BS>.

User interface of the plugin is a window with a list view.
Its status line contains important symbolic information:

| UTF8 | ASCII | List        | Description               |
| ---- | ----- | ----------- | ------------------------- |
| `⌗`    | `#`     | All         | Vim-CtrlSpace logo symbol |
| `?`    | `?`     | All         | Help Mode indicator       |
| `›_‹`  | `[_]`   | All         | Search Mode indicator     |
| `•`    | `SIN`   | Buffer      | Single Mode indicator     |
| `★`    | `VIS`   | Buffer      | Visible Mode indicator    |
| `፨`    | `ALL`   | Buffer      | All Mode indicator        |
| `○`    | `FILE`  | File        | File List indicator       |
| `⁺²`   | `+2`    | Buffer/File | Next Tab Mode indicator   |
| `⌕`    | `*`     | Buffer/File | Zoom Mode indicator       |
| `▫▪▫`  | `-+-`   | Tab         | Tab List indicator        |
| `⬆`    | `|*|`   | Workspace   | Workspace Load Mode       |
| `⬇`    | `[*]`   | Workspace   | Workspace Save Mode       |
| `♥`    | `BM`    | Bookmark    | Bookmark List indicator   |

Items listed in the plugin window can have additional indicators
(following the item text):

| UTF8 | ASCII | Indicator                         |
| ---- | ----- | --------------------------------- |
| `+`    | `+`     | Item modified                     |
| `★`    | `*`     | Item active                       |
| `☆`    | `-`     | Item visible or previously active |

Those indicators can be configured via |g:CtrlSpaceSymbols| variable.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

4.1 Status Line                                      *ctrlspace-status-line*

Vim-CtrlSpace requires a status bar. If you are using a plugin customizing
the status bar this might be a bit tricky. For example `vim-airline`
(https://github.com/bling/vim-airline) plugin might require you to set
option: >

    let g:airline_exclude_preview = 1
<
`LightLine` (https://github.com/itchyny/lightline.vim) will require to use
custom status line segments, provided by Vim-CtrlSpace API.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

4.2 Tabline                                              *ctrlspace-tabline*

Vim-CtrlSpace can set a custom tabline for you, if |g:CtrlSpaceUseTabline|
is enabled. Tabs in the tabline are displayed in the following way
(similar format is used also in the Tab List):

| Format | Tab number | Buffers | Modified | Buffer or tab name |
| ------ | ---------- | ------- | -------- | ------------------ |
| UTF8   | `1`          | `²`       | `+`        | `[README.md]`        |
| ASCII  | `1`          | `:2`      | `+`        | `[README.md]`        |

If GUI tabs are detected, this option will also set the proper function to
|guitablabel|.

Intensive tabs usage makes the tabline feature less usable, because window
can only display limited amount of tabs especially with long names.

Tab List is a solution to that problem so you can even turn off the
tabline completely: >

    set showtabline=0
<
To see Tab List press <l> in the plugin window.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

4.3 Project Root                                    *ctrlspace-project-root*

Some plugin features require a project directory to work properly. If you
open the File List for the first time in a given Vim working directory
(CWD) it will try to figure out the possible project root directory.

First, it starts in the Vim current working directory and checks for so
called "root markers". The root markers are characteristic directories
that are available in an exemplary project root directory (like `.git` or
`.hg`...). You can define them yourself in the
|g:CtrlSpaceProjectRootMarkers| variable.

If no markers were found the plugin will check if CWD is a known root. The
known roots are those directories you provided (accepted) yourself.

If the current directory is not a project root the algorithm will repeat
the whole procedure in the parent directory.

After checking all parent directories plugin will ask you to provide the
root folder explicitly. After your acceptance your choice will be stored
permanently in the `.cs_cache` file.

The `.cs_cache` file is created inside a folder specified by
|g:CtrlSpaceCacheDir|. By default it's set to your home directory

If you add a directory to bookmarks, it will be considered as a project
root automatically. Interestingly bookmarks are stored in the same cache
file.

                                                             |ctrlspace-toc|
==========================================================================

5. Lists                                                   *ctrlspace-lists*

CtrlSpace has 5 lists:

 * Buffer List (<h> for Home)
 * File List (<o> for Open)
 * Tab List (<l> for Lists)
 * Workspace List (<w>)
 * Bookmark List (<b>)

To open CtrlSpace window press <C-Space>. By default Buffer List will
open. Keys <h>, <o>, <l>, <w>, <b> when pressed again toggle between
current and previous list. Similarly <BS> works the same way.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.1 Buffer List                                      *ctrlspace-buffer-list*

Displays buffers from:

 * the current tab (Single Mode)
 * visible buffers (Visible Mode <*>)
 * all available buffers (All Mode <a>)

Buffers in Vim can have various "properties". The plugin displays only
certain buffers: "listed" (|buflisted|) and named ones. Unnamed buffers are
diplayed only when visible in the current tab or contain unsaved changes
(|modified|). This restriction prevents from accidentally diplaying
technical buffers of other plugins - not intended to be shown.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.1.1 Single Mode                                    *ctrlspace-single-mode*

| UTF8 | ASCII |
| ---- | ----- |
| `•`    | `SIN`   |

Displays only buffers related to the current tab. By related I mean
precisely "seen by (or shown in) this tab at least once". Such related
buffers are present in a buffer list kept by this tab (and available in
the Single Mode). The Single name refers to the fact we are browsing only
a list of this tab.

You can also "forget" a buffer by pressing <f>. Forgetting means
detaching, making unrelated, or just making foreign to the given tab. Such
buffer might be related to other tabs instead or might be unrelated to any
tab. Then it would only be available through the "All Mode" (press <a>).

Forgotten buffers unrelated to any tab are called "foreign buffers". They
can be automatically deleted (closed) by pressing <F>. You can also
collect them in an automatic tab by pressing <f> in the Tab List.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.1.2 Visible Mode                                  *ctrlspace-visible-mode*

| UTF8 | ASCII |
| ---- | ----- |
| `★`    | `VIS`   |

Narrows down Single Mode to only visible buffers. For example if you have
3 files in the tab and window is vertically split (displaying two files)
only those 2 files will be displayed in the list.

You can easily move between visible windows with <Tab>. By <S-Tab> you can
move to window and go back to the plugin. This action results in changing
the active window on which plugin will operate.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.1.3 All Mode                                          *ctrlspace-all-mode*

| UTF8 | ASCII |
| ---- | ----- |
| `፨`    | `ALL`   |

Displays buffers from all tabs together with foreign buffers. Practically
it displays all possible buffers similarly to |:ls| command.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.2 File List                                          *ctrlspace-file-list*

| UTF8 | ASCII |
| ---- | ----- |
| `○`    | `FILE`  |

Displays all files in the project starting from project root
(|ctrlspace-project-root|). If the file you are looking for is not
immediately visible on the list press </> to toggle fuzzy-search mode
(|ctrlspace-search-mode|).

To have the most recent list of files press <r> (refresh). If you switch
git branches don't forget to refresh the list.


Troubleshooting~

If you happen to see lots of files from the outside your current project,
for example all your files from home directory, probably you set by an
accident a root mark in your home directory. To fix that, open
`~/.cs_cache` and remove bookmark and project root entries that were
added by mistake.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.3 Tab List                                            *ctrlspace-tab-list*

| UTF8 | ASCII |
| ---- | ----- |
| `▫▪▫`  | `-+-`   |

Tabs in Vim-CtrlSpace are considered as lists of related buffers still
remaining regular Vim tab pages. They can display buffers in split
windows, be moved, copied, deleted, named, extracted, switched, and so on.

The plugin lets you perform many classic tab actions easily in the Tab
List by pressing letter <l> (for `L`ists - since tab pages are simply
seperate buffer lists).

Tabs, due to this plugin nature, are used more extensively than in a
typical Vim usage. Vim author, Bram Moolenaar in his great talk "7 Habits
of Effective Text Editing" (http://www.youtube.com/watch?v=p6K4iIMlouI)
stated that if you needed more than 10 tabs then probably you were doing
something wrong. This in not the case in Vim-CtrlSpace where tab pages are
labelled containers for buffers.

Therefore the default tabline used in Vim for organizing tab pages is not
sufficient. For example, you might have more tabs with long labels which
don't fit the tabline width, causing rendering problems.

It's recommended to turn off the tabline entirely (via Vim |showtabline|
option) and stick only to the Tab List.

Tabs can be (re)named (<=> or <m>, and <_>). Labelled tabs containing more
than one buffer can be closed (<c>) after a confirmation (except automatic
tabs). Automatic tabs are labelled tabs created automatically by the
plugin as a result of copying (<y>), collecting unsaved buffers (<u>), or
collecting foreign buffers (<f>).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.4 Workspace List                                *ctrlspace-workspace-list*

| UTF8 | ASCII | Mode      |
| ---- | ----- | --------- |
| `⬆`    | `|*|`   | Load Mode |
| `⬇`    | `[*]`   | Save mode |

The plugin allows you to save and load workspaces. A workspace is a set of
opened windows, tabs, and buffers. The Workspace List shows you available
workspaces for a given project. By default this list is displayed in the
Load Mode. To open Workspace List press <w>. Then press <s> to select the
mode (toggles between Save and Load modes), <m>, <=> to rename, and <d> to
delete.

The word "workspace" can be considered a synonym of a "session". The
ability of having so many sessions available at hand creates a lot of
interesting use cases! For example, you can have a workspace for each task
or feature you are working on. It's very easy to switch from one workspace
to another.

You can easily append any workspace to your current one (press <a>).
Moreover, you can have special workspaces prepared to be appended to
others. In that way you are able to reuse common and repetative sets of
tabs and files in many contexts.

Workspaces are saved in a file (`.cs_workspaces`) inside the project
directory. Its exact name and path is determined by configuration.

It's also possible to automatically load the last active workspace on Vim
startup and save active workspace on Vim exit. See
|g:CtrlSpaceLoadLastWorkspaceOnStart| and |g:CtrlSpaceSaveWorkspaceOnExit|
for more details.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

5.5 Bookmark List                                  *ctrlspace-bookmark-list*

| UTF8 | ASCII |
| ---- | ----- |
| `♥`    | `BM`    |

Bookmark List can be treated as a favorite project list. With bookmarks
you can easily jump between different directory locations (changes Vim
CWD).

Each project directory contains naturally a different file list, different
workspace list, etc. Nothing prevents you to mix buffers between various
projects - you can, for example jump to previous project, open a
configuration file, and return to your current stuff with that file open.

To see the Bookmark List press <b>. To add a bookmark - press <a>, to edit
the target directory - <e>. You can also rename it with <m> and <=>.

It's worth to mention, that you can still navigate to different places
manually, with the |:cd| command. The plugin will behave the same way.
In fact, jumping with Bookmark List is just like a shortcut for the |:cd|
command.


Cool Tip~

Another smart way of changing directory is jumping to a directory of given
buffer (file) by pressing <i> in the Buffer List. It's useful if you have
files from two or more different projects. To go (jump) back press <I>.

                                                             |ctrlspace-toc|
==========================================================================

6. Common Modes                                     *ctrlspace-common-modes*

Common modes are available in more than one list.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

6.1 Zoom Mode                                          *ctrlspace-zoom-mode*

| UTF8 | ASCII |
| ---- | ----- |
| `⌕`    | `*`     |

Zoom Mode works for Buffer and File Lists. To toggle Zoom Mode on press
<z>. Then press <Space> to maximize buffer that is highlighted in the
list. Pressing <Space> doesn't add buffer to the current tab – if you want
to add it press <CR>. To exit Zoom Mode press <z> again.

When entering Zoom Mode your current position and list is remembered and
reverted on exiting.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

6.2 Next Tab Mode                                  *ctrlspace-next-tab-mode*

| UTF8 | ASCII |
| ---- | ----- |
| `⁺²`   | `+2`    |

Similarly like the Zoom Mode, Next Tab Mode works in File and Buffer
Lists. It can be turned on with the uppercase <T> letter (or <C-t>). If
the mode is active, <T> creates the new tab only once (that would be a
next tab to the current one) and add all files / buffers to that tab. This
is opposite to <t> which opens things in a new tab every time. If you
want to create a new tab but stay in the Next Tab Mode press <C-t>.

The mode indicator shows you the number of buffers opened in the next tab.
You can jump to that tab anytime with <]> key.

This mode allows for bulk opening files or buffers in subsequent tabs.
That way you can easily extract given items to separate tabs.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

6.3 Search Mode                                      *ctrlspace-search-mode*

| UTF8 | ASCII |
| ---- | ----- |
| `›_‹`  | `[_]`   |

This mode can be triggered by </> or by a capital letter of given list
(<H>, <O>, <L>, <W>, <B>). In that mode you can enter a search text. This
will narrow the list content and sort items by relevance (the highest
score - the lowest position). To finish entering press <CR> or </>. If you
press <Tab> instead, your text will be accepted and followed immediately
(just like pressing <CR> twice). To see full key reference during query
entering press <?>.

To clear the search query press <BS>. To use previous queries from history
press <C-p> (previous) or <C-n> (next).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

6.4 Nop Mode                                            *ctrlspace-nop-mode*

Nop (Non-Operational) Mode happens when for example there are no items to
show (empty list), or you are trying to type a search query, and there are
no results at all.

To see what are the rescue options from a Nop Mode check <?>.
Sometimes it would be <BS> removing search query, sometimes switching to
different list (<h>, <o>, <l>, <w>, or <b>).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

6.5 Help Mode                                          *ctrlspace-help-mode*

Help Mode is a view showing available keys together with their
descriptions, depending on your current list and modes. You can toggle
Help Mode in any view by pressing <?>.

                                                             |ctrlspace-toc|
==========================================================================

7. Configuration                                   *ctrlspace-configuration*

Vim-CtrlSpace has many configuration options. To alter any of them, define
it as global variables in your `.vimrc` file in the similar form: >

    let g:CtrlSpaceFooBar = 123
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.1 *g:CtrlSpaceHeight*

Sets the minimal height of the plugin window. Default value: >

    let g:CtrlSpaceHeight = 1
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.2 *g:CtrlSpaceMaxHeight*

Sets the maximum height of the plugin window. If `0` is provided it uses 1/3
of the screen height. Default value: >

    let g:CtrlSpaceMaxHeight = 0
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.3 *g:CtrlSpaceSetDefaultMapping*

Turns on the default mapping. If you turn off this option (`0`) you will
have to provide your own mapping to trigger the plugin. Default value: >

    let g:CtrlSpaceSetDefaultMapping = 1
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.4 *g:CtrlSpaceDefaultMappingKey*

By default, Vim-CtrlSpace maps itself to <C-Space>. If you want to change
the default mapping provide it here as a string with valid Vim keystroke
notation. Default value: >

    let g:CtrlSpaceDefaultMappingKey = "<C-Space>"
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.5 *g:CtrlSpaceKeys*

You can provide your own functions and override default key bindings in
that way. The |g:CtrlSpaceKeys| can store a dictionary, where keys could be
lists or modes, accordingly:

 * `"Search"`
 * `"Help"`
 * `"Nop"`
 * `"Buffer"`
 * `"File"`
 * `"Tab"`
 * `"Workspace"`
 * `"Bookmark"`

Values are dictionaries with key mappings and function names. Look at the
following example: >

    function! PrintFooBar(k)
        echo "Foo Bar!"
    endfunction

    let g:CtrlSpaceKeys = { "Buffer": { "a": "PrintFooBar" } }
<
This will map a function `PrintFooBar(k)` to key <a> in the buffer list.
Besides key mappings there are also available some special key classes:

 * `"lowercase"`
 * `"uppercase"`
 * `"controls"`
 * `"numbers"`
 * `"specials"`

Default value: >

    let g:CtrlSpaceKeys = {}
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.6 *g:CtrlSpaceHelp*

Allows you to provide a help description for your custom functions.
Contains a dictionary with keys holding function names and values
containing their descriptions. They will be displayed in the Help
Mode. Example: >

    let g:CtrlSpaceHelp = { "PrintFooBar": "Print foo bar!" }
<
Default value: >

    let g:CtrlSpaceHelp = {}
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.7 *g:CtrlSpaceGlobCommand*

If not empty, the provided command will be used to list all files instead
of Vim |globpath()| function. For example, if you have `Ag` installed that
could be: >

    if executable("ag")
        let g:CtrlSpaceGlobCommand = 'ag -l --nocolor -g ""'
    endif
<
Default value: >

    let g:CtrlSpaceGlobCommand = ""
<

Cool Tip~

You can even make `Ag` to show hidden files by providing `--hidden` option: >

    let g:CtrlSpaceGlobCommand = 'ag -l --hidden --nocolor -g ""'
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.8 *g:CtrlSpaceUseTabline*

Should Vim-CtrlSpace change your default tabline to its own?

Default value: >

    let g:CtrlSpaceUseTabline = 1
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.9 *g:CtrlSpaceUseMouseAndArrowsInTerm*

Should the plugin use mouse, arrows and <Home>, <End>, <PageUp>,
<PageDown> keys in a terminal Vim. Disables the <Esc> key if turned on.

Default value: >

    let g:CtrlSpaceUseMouseAndArrowsInTerm = 0
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.10 *g:CtrlSpaceSaveWorkspaceOnExit*

Saves the active workspace (if present) on Vim quit. If this option is
set, the Vim quit (<Q>) action in the plugin does not check for workspace
changes.

Default value: >

    let g:CtrlSpaceSaveWorkspaceOnExit = 0
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.11 *g:CtrlSpaceSaveWorkspaceOnSwitch*

Saves the active workspace (if present) on switching to another workspace
or clearing (closing) the current one. If this option is set, the plugin
won't warn you about an unsaved workspace.

Default value: >

    let g:CtrlSpaceSaveWorkspaceOnSwitch = 0
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.12 *g:CtrlSpaceLoadLastWorkspaceOnStart*

Loads the last active workspace (if found) on Vim startup.

Default value: >

    let g:CtrlSpaceLoadLastWorkspaceOnStart = 0
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.13 *g:CtrlSpaceCacheDir*

A directory for the Vim-CtrlSpace cache file (`.cs_cache`). By default
your `$HOME` directory will be used.

Default value: >

    let g:CtrlSpaceCacheDir = expand($HOME)
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.14 *g:CtrlSpaceProjectRootMarkers*

An array of directory names which presence indicates the project root. If
no marker is found, you will be asked to confirm the project root
depending on the current working directory. Use empty array to disable
this functionality.

Markers will be also used as a storage for `cs_workspaces` (workspaces of
the current project) and `cs_files` (cached files of the current project).

Default value: >

    let g:CtrlSpaceProjectRootMarkers = [
         \ ".git",
         \ ".hg",
         \ ".svn",
         \ ".bzr",
         \ "_darcs",
         \ "CVS"
         \ ]
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.15 *g:CtrlSpaceUseUnicode*

Set to `1` if you want to use Unicode symbols, or `0` otherwise.

Default value: >

    let g:CtrlSpaceUseUnicode = 1
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.16 *g:CtrlSpaceSymbols*

Enables you to provide your own symbols. It's useful if, for example, your
font doesn't contain enough symbols or the glyphs are poorly rendered.

Vim-CtrlSpace uses the following defaults:

| Symbol | UTF8 | ASCII |
| ------ | ---- | ----- |
| `CS`     | `⌗`    | `#`     |
| `Sin`    | `•`    | `SIN`   |
| `All`    | `፨`    | `ALL`   |
| `Vis`    | `★`    | `VIS`   |
| `File`   | `○`    | `FILE`  |
| `Tabs`   | `▫`    | `-`     |
| `CTab`   | `▪`    | `+`     |
| `NTM`    | `⁺`    | `+`     |
| `WLoad`  | `⬆`    | `|*|`   |
| `WSave`  | `⬇`    | `[*]`   |
| `Zoom`   | `⌕`    | `*`     |
| `SLeft`  | `›`    | `[`     |
| `SRight` | `‹`    | `]`     |
| `BM`     | `♥`    | `BM`    |
| `Help`   | `?`    | `?`     |
| `IV`     | `☆`    | `-`     |
| `IA`     | `★`    | `*`     |
| `IM`     | `+`    | `+`     |
| `Dots`   | `…`    | `...`   |

You can define your own symbols like in this example: >

    let g:CtrlSpaceSymbols = { "File": "◯" }
<
Default value: >

    let g:CtrlSpaceSymbols = {}
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.17 *g:CtrlSpaceIgnoredFiles*

The expression used to ignore some files during file collecting. It is
used in addition to the `wildignore` option in Vim (see |wildignore|).
The `wildignore` option won't work with a custom glob command
(|g:CtrlSpaceGlobCommand|). The glob command may ignore some files
itself (for example: `Ag` command obeys `.gitignore` file).

Default value: >

    let g:CtrlSpaceIgnoredFiles = '\v(tmp|temp)[\/]'
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.18 *g:CtrlSpaceStatuslineFunction*

Allows to provide custom statusline function used by the CtrlSpace window.

Default value: >

    let g:CtrlSpaceStatuslineFunction = "ctrlspace#api#Statusline()"
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.19 *g:CtrlSpaceSearchTiming*

Allows you to adjust search smoothness by providing a delay on search
input. By default the delay is set to 200 ms. That way the plugin ensures
smooth search input behavior.

Default value: >

    let g:CtrlSpaceSearchTiming = 200
<
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

7.20 *g:CtrlSpaceFileEngine*

The plugin provides fuzzy search engine written in Go and compiled for
several architectures:

 * `file_engine_darwin_386`
 * `file_engine_darwin_amd64`
 * `file_engine_freebsd_386`
 * `file_engine_freebsd_amd64`
 * `file_engine_freebsd_arm`
 * `file_engine_linux_386`
 * `file_engine_linux_amd64`
 * `file_engine_linux_arm`
 * `file_engine_netbsd_386`
 * `file_engine_netbsd_amd64`
 * `file_engine_netbsd_arm`
 * `file_engine_openbsd_386`
 * `file_engine_openbsd_amd64`
 * `file_engine_windows_386.exe`
 * `file_engine_windows_amd64.exe`

The engine protocol is relatively simple and it's possible to implement an
engine in any technology (see |ctrlspace-engine-specs|). The engine
must be provided as an executable file in the `bin` directory in the plugin
folder.

To enable your custom engine provide the executable name as a string to
|g:CtrlSpaceFileEngine| variable. You can also force plugin to use
a certain implementation of your choice. For example, a Go version
for Mac OS X could look like: >

    let g:CtrlSpaceFileEngine = "file_engine_darwin_amd64"
<
Another way of enabling a Go implementation is file engine auto detection.
Plugin can try to infer matching os and architecture and use proper Go
binary. To enable it provide a string `"auto"` (or leave default value): >

    let g:CtrlSpaceFileEngine = "auto"
<
To make sure a correct file engine is in use check the Help View (<?>).

To disable external file engines and stick to pure Vim implementation,
just provide an empty string: >

    let g:CtrlSpaceFileEngine = ""
<
Default value: >

    let g:CtrlSpaceFileEngine = "auto"
<
                                                             |ctrlspace-toc|
==========================================================================

8. API                                                       *ctrlspace-api*

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1 Commands                                            *ctrlspace-commands*

At the moment Vim-CtrlSpace provides you 10 commands:

 * |:CtrlSpace|
 * |:CtrlSpaceGoUp|
 * |:CtrlSpaceGoDown|
 * |:CtrlSpaceTabLabel|
 * |:CtrlSpaceClearTabLabel|
 * |:CtrlSpaceSaveWorkspace|
 * |:CtrlSpaceNewWorkspace|
 * |:CtrlSpaceLoadWorkspace|
 * |:CtrlSpaceAddProjectRoot|
 * |:CtrlSpaceRemoveProjectRoot|

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.1 *:CtrlSpace* [keys]

Shows the plugin window. It is meant to be used in custom mappings or more
sophisticated plugin integration. You can pass keys that will be "pressed"
in the plugin window.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.2 *:CtrlSpaceGoUp*

Opens the previous buffer from the current Buffer List in Single Mode
(without opening the plugin window).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.3 *:CtrlSpaceGoDown*

Opens the next buffer from the current Buffer List in Single Mode (without
opening the plugin window).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.4 *:CtrlSpaceTabLabel*

Allows you to change (or add/remove) a custom tab name.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.5 *:CtrlSpaceClearTabLabel*

Removes a custom tab label.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.6 *:CtrlSpaceSaveWorkspace* [workspace]

Saves the workspace with a given name. If no name is provided then it
saves the active workspace (if present).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.7 *:CtrlSpaceNewWorkspace*

Closes all opened buffers and the active workspace (if any) and leaves
only one tab and one buffer, as in a fresh Vim instance. This is useful if
you want to create an empty workspace.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.8 *:CtrlSpaceLoadWorkspace* [!] [workspace]

Loads the workspace with a given name. It has also a banged version
( *:CtrlSpaceLoadWorkspace!* ) which performs appending instead of
loading. If no name is given then it loads (or appends) the active
workspace (if present).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.9 *:CtrlSpaceAddProjectRoot* [directory]

Add a given directory as a permanent project root. It's useful when, for
example project root markers are missing or available on a too higher
level of a hierarchy. If no directory is given the current working
directory is used instead.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.1.10 *:CtrlSpaceRemoveProjectRoot* [directory]

Removes a given directory from permanent project root collection. If no
directory is given the current working directory is used instead.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2 Functions                                          *ctrlspace-functions*

Almost all Vim-CtrlSpace function are public and accessible from any
place. However some of them in the `ctrlspace#api` namespace are designed
for external integration with the plugin internals.

You can use those API functions for seamless status line or tabline
integration, or just for more advanced interactions with other plugins.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.1 ctrlspace#api#BufferList({tabnr})         *ctrlspace#api#BufferList()*

Returns a list of buffers available in a given tab. The list is sorted
in the same order like in the CtrlSpace Buffer List window.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.2 ctrlspace#api#Buffers({tabnr})               *ctrlspace#api#Buffers()*

Returns a dictionary of buffer number and name pairs for a given tab. This
is the content of the internal buffer list belonging to the specified tab.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.3 ctrlspace#api#TabModified({tabnr})       *ctrlspace#api#TabModified()*

Returns `1` if given tab contains a modified buffer, `0` otherwise.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.4 ctrlspace#api#Statusline()                *ctrlspace#api#Statusline()*

Provides a custom statusline string used by plugin window.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------
                                      *ctrlspace#api#StatuslineTabSegment()*
8.2.5 ctrlspace#api#StatuslineTabSegment()

Returns the info about the current tab (tab number, label, etc.). It is
useful if you don't use the custom tabline string (or perhaps you have set
|showtabline| to `0` (see |showtabline| for more info)).

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------
                                     *ctrlspace#api#StatuslineModeSegment()*
8.2.6 ctrlspace#api#StatuslineModeSegment({...})

Returns the info about the plugin mode. It can take an optional separator.
It can be useful for a custom status line integration (e.g. in plugins
like LightLine (https://github.com/itchyny/lightline.vim))

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------
                                          *ctrlspace#api#TabBuffersNumber()*
8.2.7 ctrlspace#api#TabBuffersNumber({tabnr})

Returns formatted number of buffers belonging to given tab. Formats the
output as small Unicode characters (upper indexes) or regular ASCII number
characters (depending on |g:CtrlSpaceUseUnicode| setting). It is a helper
function useful if you want to provide your own tabline function
implementation.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------
                                                  *ctrlspace#api#TabTitle()*
8.2.8 ctrlspace#api#TabTitle({tabnr}, {bufnr}, {bufname})

A helper function returning a consistent title for a given tab. If the tab
does not have a custom title, then the title based on passed buffer number
and buffer name is returned instead.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.9 ctrlspace#api#Guitablabel()              *ctrlspace#api#Guitablabel()*

Provides a custom label for GVim tabs.

                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.10 ctrlspace#api#Tabline()                     *ctrlspace#api#Tabline()*

Provides a custom tabline string.

Useful, for example, to show the current work dir in the tabline by adding
the following scriplet to ~/.vimrc:

function! CWDTabline()
    let tabline=''
    let tabline.='%#TabLineFill#'
    let tabline.='%=|'      "left/right separator
    let tabline.='%#identifier#'
    let tabline.='%.30(%{fnamemodify(getcwd(), ":~")}%)'
    let tabline.='%*'

    return tabline
endfunction

function! MyTabline()
  return ctrlspace#api#Tabline().CWDTabline()
endfunction

set tabline=%!MyTabline()
set showtabline=2
                                                             |ctrlspace-toc|
--------------------------------------------------------------------------

8.2.11 ctrlspace#api#BufNr()                         *ctrlspace#api#BufNr()*

Returns the current plugin buffer number if the plugin is visible or `-1`
otherwise.

                                                             |ctrlspace-toc|
==========================================================================

9. File Engine Specifications                       *ctrlspace-engine-specs*

It's fairly easy to provide your own implementation of a fuzzy searcher
for files. The main reason for enabling such external searcher is the
limited speed of Vim Script processing.

Moreover the amount of data returned by the search algorithm is
significantly greater than in other popular fuzzy searchers implemented in
pure Vim Script (like `CtrlP`) thus it affects the performance too.


General Assumptions~

By default the plugin shows at most 500 items per list and 200 when fuzzy
searched. That rule is enforced by internal fuzzy searcher implementation
and by the external engine written in Go.

More items make the plugin window sluggish and inconvenient to browse. If
something you are looking for is not immediately available within those
limits then most likely you should refine your search criteria.

Of course your are not forced to follow those limitations. Feel free to
change the limits in your own implementation if you think it would work
better for you.

The external engine is designed specifically for searching and displaying
files. All other search in the plugin is performed by an internal engine.
The communication with external processes involves some latency as Vim
must execute an external command in the system shell.

However, such latency is acceptable for files, where we might have a great
volume to search and show. It is much less likely that you hit thousands
of buffers, tabs, workspaces, or bookmarks. But for files that is a common
scenario on everyday basis.

The responsibility of an external engine is also to render the exact
response - text that would be displayed in the plugin window together with
all metadata that allow plugin proceed it further. This is because of the
massive scale of processing needed in case of files. The engine technology
is assumed to be a lot faster than Vim Script with string concatenation
either.


The Request~

The plugin attempts to query data by executing the engine program and
passing just a single line of text to the program Standard Input (`STDIN`).
That line contains an object definition in JSON format describing the
current context of Vim-CtrlSpace.

The JSON object has the following structure (with sample data): >

    {
        "Query":    "gfx",
        "Columns":  170,
        "Limit":    0,
        "Source":   "/Users/szw/Projects/vim-ctrlspace/.git/cs_files",
        "Dots":     "…",
        "DotsSize": 1
    }
<
The fields mean:

 * `Query`    - Characters placed in the plugin search input
              (`[A-Za-z0-9]`). The query might be empty - then the engine
              should just display items.

 * `Columns`  - The width of the plugin window. Lines rendered in the
              response should have extact width provided by this value.

 * `Limit`    - If greater than 0 then results should be trimmed to that
              value - otherwise they should follow 500 / 200 rule.
              The limit is used while Search Mode is enabled. In that
              mode you cannot move the bar and browse List View.
              Since you are just supposed to type search characters
              there is no point to render more items than would be visible
              at that moment.

 * `Source`   - The path to file containing list to files to be searched.
              The source is a text file containg file paths. Each line
              is a separate file path. The line number minus 1 is
              considered as a correspondent index value.

 * `Dots`     - The character(s) used to trim the item text that exceeds
              plugin window width. See also |g:CtrlSpaceSymbols|.

 * `DotsSize` - The visual size of the `Dots` symbol.


The Response~

The engine should generate output to its Standard Output (`STDOUT`). The
expected response should be composed of a few lines. Each line provides
different type of data and metadata. A sample response might look like
this one: >

    ["gfx"]
    [31,44]
    2
      gfx/cs5_window.png
      gfx/logo5.png
<
The first line should contain unique search patterns that will be used to
highlight search results with `CtrlSpaceSearch` group. Those patterns
should be expressed as a |list| definition in Vim Script, for example: >

    ["gfx"]
<
The second line must be a list of indices (line numbers of the source file
minus 1) sorted accordingly to search algorithm relevance (reversed).
This order should also match to the order of text lines explained below.
The list should be formatted as a Vim Script |list|: >

    [31,44]
<
Third line is the results size: >

    2
<
The next lines are just content lines. They must be of size given by
context `Columns` field. That means all remaining characters should be
filled with spaces (`'` `'`). Also first 2 and last 3 characters of each
line should be always blank spaces. That format is strictly required
by plugin rendering algorithm: >

      gfx/cs5_window.png
      gfx/logo5.png
<
The order reflects the reversed results relevance. The most relevant items
should be placed at the bottom (as last ones).

                                                             |ctrlspace-toc|
==========================================================================

10. Authors and License                      *ctrlspace-authors-and-license*

Copyright (c) 2013-2015 Szymon Wrozynski and Contributors.

 * https://github.com/szw/vim-ctrlspace/commits/master

Licensed under MIT License conditions.

 * https://github.com/szw/vim-ctrlspace/blob/master/plugin/ctrlspace.vim#L5-L26

Vim-CtrlSpace is inspired by Robert Lillack plugin VIM bufferlist (c) 2005
Robert Lillack. Moreover some concepts and inspiration has been taken from
Vim-Tabber by Jim Steward and Tabline by Matthew Kitt.

Special thanks to Wojtek Ryrych (https://github.com/ryrych) for help and
patience ;) and all Contributors.

                                                             |ctrlspace-toc|
==========================================================================

vim:tw=74:ts=4:ft=help:norl: