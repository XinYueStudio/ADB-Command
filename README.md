# ADB-Command

所有应用:
   
   adb shell pm list packages
        
        
   
        package:com.android.smoketest

        package:com.example.android.livecubes

        package:com.android.providers.telephony

        package:com.google.android.googlequicksearchbox

        package:com.android.providers.calendar

        package:com.android.providers.media

        package:com.android.protips

        package:com.android.documentsui

        package:com.android.gallery

        package:com.android.externalstorage

        ...

        // other packages here

        ...
    
    
    
系统应用:
  
    adb shell pm list packages -s
   
   
第三方应用:

     adb shell pm list packages -3
   
   
包名包含某字符串的应用(比如要查看包名包含字符串 xinyuestudio 的应用列表):

      adb shell pm list packages xinyuestudio
   
     adb shell pm list packages | grep xinyuestudio
   
   
   
   
安装 APK:

     adb install [-lrtsdg] <path_to_apk>

参数：

adb install 后面可以跟一些可选参数来控制安装 APK 的行为，可用参数及含义如下：

        参数	含义

        -l	将应用安装到保护目录 /mnt/asec

        -r	允许覆盖安装

        -t	允许安装 AndroidManifest.xml 里 application 指定 android:testOnly="true" 的应用

        -s	将应用安装到 sdcard

        -d	允许降级覆盖安装

        -g	授予所有运行时权限

   
   
卸载应用:   

     adb uninstall [-k] <packagename>
    
    
清除应用数据与缓存:

    adb shell pm clear <packagename>
    
    
查看前台 Activity:

     adb shell dumpsys activity activities | grep mFocusedActivity
   
   
查看正在运行的 Services:

     adb shell dumpsys activity services [<packagename>]
    
    
启动应用/ 调起 Activity:

     adb shell am start [options] <INTENT>
    
    
调起 Service:

     adb shell am startservice [options] <INTENT>


停止 Service :

     adb shell am stopservice [options] <INTENT>
    

发送广播:
   
     adb shell am broadcast [options] <INTENT>
    
    
强制停止应用:
   
    adb shell am force-stop <packagename>
    

 查看日志:

[adb] logcat [<option>] ... [<filter-spec>] ...
    
    按级别过滤日志
    
    Android 的日志分为如下几个优先级（priority）：

    V —— Verbose（最低，输出得最多）
    
    D —— Debug
    
    I —— Info
    
    W —— Warning
    
    E —— Error
    
    F —— Fatal
    
    S —— Silent（最高，啥也不输出）
    

  查看设备信息型号:
  
     adb shell getprop ro.product.model
   
   
  电池状况:
  
    adb shell dumpsys battery
   
   
  屏幕分辨率:
  
     adb shell wm size
   
   
  屏幕密度pdi:
  
    adb shell wm density
   
   
  显示屏参数:
  
    adb shell dumpsys window displays
   
   
 CPU 信息:
 
    adb shell cat /proc/cpuinfo
   
   
 内存信息:
  
    adb shell cat /proc/meminfo
   
   
屏幕截图:

 截图保存到电脑
 
        adb exec-out screencap -p > sc.png
   
   如果 adb 版本较老，无法使用 exec-out 命令，这时候建议更新 adb 版本。无法更新的话可以使用以下麻烦点的办法：
   先截图保存到设备里
        
        adb shell screencap -p /sdcard/sc.png
   
   然后将 png 文件导出到电脑
   
        adb pull /sdcard/sc.png
 
 
 
 检测设备是否已 root:
   
       adb shell
       
       su
       
       
 重启手机：
    
      adb reboot
      
      
      
 性能测试_FPS：     
 
     adb shell dumpsys gfxinfo packageName
   
