---
tags:
  - Work_Tie_In
  - How_to_Learn_a_New_Language
---
All functional code located within 'packages' directory which is further organised into sub-directories e.g. api, tests, ui, components, map, etc

Within the 'map' directory are 'lib' and 'src' directories - code is written in the 'src' directory while 'lib' holds things like hooks and interfaces which should not generally be changed

map's src directory is further organised with main map, container, and style files at the top level and other files stored within organised subdirectories such as components, tests, reducers, etc.

Most common to work within components directory with is again organised by component (which may or may not have sub-components inside). Organisation within component directories varies depending on need with some including tests directories while others have their unit tests within the src/tests directory. 