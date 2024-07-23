winzip.com/en/product/command-line
https://download.winzip.com/wzcline60-32.msi
https://download.winzip.com/wzcline60-64.msi

因为还要带WinZip，所以绿化一下（x86也大同小异）：
:FATAL ERROR: WinZip is not properly installed. Please re-install WinZip
reg add "HKCU\Software\Nico Mak Computing\WinZip\WinIni" /f
:FATAL ERROR: assert failure (util.cpp@944)
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths\WINZIP64.EXE" /ve /d 0 /f
WZ(UN)ZIP
rd %allusersprofile%\WinZip
搜索字符串SOFTWARE\，发现整个过程是俩函数，各有俩地方CALL它，断首RET上面俩reg下面rd自动也逆了

去遇致命错误会生成wzCLine.rpt文件在桌面：
搜索字符串wzCLine.rpt，发现整个过程是函数，有很多地方CALL它，断首RET

去THANK YOU FOR TRYING WINZIP COMMAND LINE ADD-ON：
命令行启动WZZIP a可以看到，还无法不再提示，本去除不影响-yp参数
x96dbg>文件>附加>WZZIP或拖入WZZIP.EXE
符号>wzzip.exe
右键>搜索范围>当前模块>字符串引用>"THANK YOU FOR TRYING WINZIP COMMAND LINE ADD-ON\nThis is a fully functional version for EVALUATION USE ONLY\nThis notice is not displayed with registered Standard and Pro\neditions of WinZip. Please go to www.winzip.com to order WinZip."
*：下面可以看到&L"(press any key to continue (Ctrl-C to quit))"
1.上面JNE改JMP，文件>补丁
2.再上面找INT3选中下一条指令Ctrl+R，NOP
2.1在2上一条是JE，改JMP或全NOP

WARNING: the selected compression expects a .zipx extension, you specified .zip时机：
PPMd算法（-ep）、LZMA算法（-el）、BZip2（-eb）、-ez Jpeg算法、WavPack等
7-Zip不支持：-ez Jpeg算法、-et zstd-wz算法

去-s弱密码报PASSWORD POLICY: Password must be at least 8 characters long.：参上
