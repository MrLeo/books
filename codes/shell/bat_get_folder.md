
```bat
@echo off&setlocal enabledelayedexpansion
title BAT获取指定目录下快捷方式的起始位置
REM set "lj=指定目录"
set "lj=%ALLUSERSPROFILE%\桌面"
for /f "delims=" %%a in ('dir/b "%lj%"') do (
   for /f "tokens=* delims=" %%i in ('type "%lj%\%%a"^|find ":\"') do (
      set /a n=n%%2+1
      if !N! equ 2 echo %%i
))
pause
```