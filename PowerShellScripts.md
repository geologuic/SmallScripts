## To generate type information and doc of pybind11 Python functions

IDEs such as Pycharm do a lot of static analyses (completion, tooltips, checks...), but may struggle for custom packages generated with pybind11 installed in virtual environments. Good news: this can be fixed easily! Before all, need to install pybind11-stubgen in your virtual environment:
```
.venv\Scripts\activate
uv pip install pybind11-stubgen
```

After that, install / upgrade the wheel (example here: ring_point_process), and generate the pyi information: 
```
uv pip install ring_pointprocess-5.6.2-cp312-cp312-win_amd64.whl
pybind11-stubgen.exe -o .\.venv\Lib\site-packages\. ring_pointprocess.ring_pointprocess_py_spp    
```
The last argument should be the name as the .pyd file (without version info) in the site-packages directory.


## To find where Qt dlls are in the PATH

```
$env:path -split ';' | Get-ChildItem | Format-Table Fullname | findstr Qt.*.dll
```

In the above command: 
 * `env:path_` returns the PATH (with ; as separators)
 * `Get-ChildItem | Format-Table Fullname` list the files under the current PATH directory, and shows the full file name
 * `findstr` looks for the substring in the full file name. Regular expression is slighly different as Linux: . means any char and * any number

## To look for DLL dependencies without installing the dependency walker

```
 & "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\dumpbin.exe" /dependents your_dll_or_exe_file
```
The '&' tells PS to call the executable. 
