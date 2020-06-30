## To find where a particular Qt dlls are in the PATH

```
$env:path -split ';' | Get-ChildItem | Format-Table Fullname | findstr Qt.*.dll
```

In the above command: 
 * `env:path_` returns the PATH (with ; as separators)
 * `Get-ChildItem | Format-Table Fullname` list the files under the current PATH directory, and shows the full file name
 * `findstr` is the PowerShell equivalent of `grep`. Regular expression is slighly different as Linux: . means any char and * any number
