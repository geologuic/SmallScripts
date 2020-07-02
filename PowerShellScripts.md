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
