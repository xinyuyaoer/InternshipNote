```bat
    @echo off
    setlocal enableDelayedExpansion

    :: 提示用户输入文件夹路径
    set /p path=Please paste/input your folder path (e.g., C:\path\to\folder) :

    :: 进入该路径
    cd /d "%path%"

    :: 通过循环修改文件夹里面的文件
    for /f "tokens=*" %%f in ('dir /b /a-d "%path%"') do (
        :: 如果文件名包含 "_纯图版"，则进行替换
        set "filename=%%f"
        ren "%%f" "!filename:_纯图版=!"
    )

    :: 完成后显示消息，并打开文件夹
    echo.
    echo Renaming is done. The files are located at: %path%
    C:\Windows\explorer.exe "%path%"

    pause
```