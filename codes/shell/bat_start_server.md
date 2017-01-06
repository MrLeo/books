
```bat
:: 加@表示连echo off都不显示，不然会显示出echo off的命令
:: REM和两个冒号(::) 是注释
@echo off 
:menu
title 各种服务开启、关闭程序 
REM **************************
REM 选择要操作的服务
REM **************************
cls
echo.
echo 开启、关闭 服务
echo -----------------------------------------
echo 1.家庭组服务（开启/关闭 ）
echo 2.SQL Server 服务（开启/关闭）
echo 0.退出
echo.
set in= 
set /p in=请输入：
if "%in%"=="0" goto end
if "%in%"=="1" goto submenu1
if "%in%"=="2" goto mssql
REM **************************
REM 家庭组服务
REM **************************
echo.
:submenu1
cls
echo.
echo 1.家庭组服务（开启/关闭 ）
echo -----------------------------------------
echo    1.开启
echo    2.关闭
echo    3.禁用
echo    4.启用（自动）
echo    5.启用（手动）
echo    6.重启
echo    0.返回
echo.
set in= 
set /p in=请输入：
if "%in%"=="0" goto menu
if "%in%"=="1" goto start-submenu1
if "%in%"=="2" goto stop-submenu1
if "%in%"=="3" goto disabled-submenu1
if "%in%"=="4" goto autostart-submenu1
if "%in%"=="5" goto demandstart-submenu1
if "%in%"=="6" goto restart-submenu1
:start-submenu1
net start HomeGroupListener
net start HomeGroupProvider
pause...
goto submenu1
:stop-submenu1
net stop HomeGroupListener
net stop HomeGroupProvider
pause...
goto submenu1
:disabled-submenu1
sc config HomeGroupListener start= disabled
sc config HomeGroupProvider start= disabled
pause...
goto submenu1
:autostart-submenu1
sc config HomeGroupListener start= auto
sc config HomeGroupProvider start= auto
pause...
goto submenu1
:demandstart-submenu1
sc config HomeGroupListener start= demand
sc config HomeGroupProvider start= demand
pause...
goto submenu1
:restart-submenu1
net stop HomeGroupListener
net stop HomeGroupProvider
net start HomeGroupListener
net start HomeGroupProvider
pause...
goto submenu1
echo.
REM **************************
REM SQL Server 服务
REM **************************
:mssql
:: 将引号内部分改成你要查找的服务名称
sc query |find /i "SQL Server (MSSQLSERVER)" >nul 2>nul
:: 如果服务存在，跳转至exist标签
if not errorlevel 1 (goto exist-mssql) else goto notexist-mssql
:exist-mssql
:: 服务存在/启动时
@echo SQL Server服务已启动...正在关闭服务...
@net stop "SQL Server (MSSQLSERVER)"
@net stop "SQL Full-text Filter Daemon Launcher (MSSQLSERVER)"
@pause...
goto end
:notexist-mssql
:: 服务不存在/停止时
@echo SQL Server服务已停止...正在启动服务...
@net start "SQL Server (MSSQLSERVER)"
@pause...
goto end
REM **************************
REM 退出
REM **************************
:end
echo 3秒后关闭
echo 倒计时：3
ping /n 2 127.1 >nul
echo 倒计时：2
ping /n 2 127.1 >nul
echo 倒计时：1
ping /n 2 127.1 >nul
exit
```