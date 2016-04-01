# SlicerMixMatchExtension

This is an example of extension bundling atypical modules.

## Modules

### ScriptedMixMatch

Scripted module building and using a c++ Loadable module logic.

Until [Slicer issue #3730](http://www.na-mic.org/Bug/view.php?id=3730) is resolved, prior instantiating the logic using `slicer.vtkSlicerScriptedMixMatchLogic()`:
 
* within Slicer core, this workaround is required:
```
import vtkSlicerScriptedMixMatchModuleLogic
setattr(slicer, 'vtkSlicerScriptedMixMatchLogic', vtkSlicerScriptedMixMatchModuleLogic.vtkSlicerScriptedMixMatchLogic)
```

* within an extension, this workaround is required:
```
import os
import sys
logic_path=os.path.join(os.path.dirname(slicer.modules.scriptedmixmatch.path), '../qt-loadable-modules')
sys.path.append(logic_path)
sys.path.append(os.path.join(logic_path, './Python'))
import vtkSlicerScriptedMixMatchModuleLogic
setattr(slicer, 'vtkSlicerScriptedMixMatchLogic', vtkSlicerScriptedMixMatchModuleLogic.vtkSlicerScriptedMixMatchLogic)
```

In both case, waiting the Slicer is resolved, approach similar to what is done in [6b6272d](https://github.com/jcfr/SlicerMixMatchExtension/commit/6b6272d512801e103cf4d4f795a22bf0be792d14) is suggested.


## Build and Run

Prerequisites: 
* [Build Slicer](http://wiki.slicer.org/slicerWiki/index.php/Documentation/Nightly/Developers/Build_Instructions)


Build:


```
cmake -DSlicer_DIR=/home/jcfr/Projects/Slicer-Release/Slicer-build/ ../SlicerMixMatchExtension
```

Run:


```
cd /home/jcfr/Projects/Slicer-Release/Slicer-build
./Slicer --additional-module-paths /home/jcfr/Projects/SlicerMixMatchExtension-Release/

```

