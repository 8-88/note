#### 错误如下:

<pre>
git pull
0 [main] us 0 init_cheap: VirtualAlloc pointer is null, Win32 error 487
AllocationBase 0x68550000, BaseAddress 0x68570000, RegionSize 0x22000, State 0x1000
f:\kenshin\DevTools\git-1.8.1.2\bin\sh.exe: *** Couldn't reserve space for cygwin's heap, Win32 error 0
</pre>

#### 解决方案:
<pre>
cd F:\kenshin\DevTools\git-1.8.1.2\bin
F:\kenshin\DevTools\git-1.8.1.2\bin>rebase.exe -b 0x50000000 msys-1.0.dll
</pre>

#### 参考：
* <http://www.trinitycore.org/f/topic/5194-msysgit-couldnt-reserve-space-for-cygwins-heap/>
* <http://stackoverflow.com/questions/18502999/git-extensions-win32-error-487-couldnt-reserve-space-for-cygwins-heap-win32>