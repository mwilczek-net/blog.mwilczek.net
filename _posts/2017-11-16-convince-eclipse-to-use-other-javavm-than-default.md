---
bg_credential: <a href="https://unsplash.com/@sarahleejs?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Jongsun Lee</a> on <a href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText" target="_blank">Unsplash</a>
bg:            "jongsun-lee-F-pSZO_jeE8-unsplash.jpg"
layout:        post
title:         "Convince Eclipse to use other JavaVM than default"
crawlertitle:  "Convince Eclipse to use other JavaVM than default"
summary:       "Eclipse with multiple JavaVMs"
date:          2017-11-16
categories:    posts
tags:          ['eclipse', 'java']
author:        "mwilczek.net"

---

Just edit `eclipse.ini` file (macOS path: `/Applications/Eclipse.app/Contents/Eclipse/eclipse.ini`). In this file, somewhere before `-vmargs` add:

```ini
--vm
/Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/bin/java
```

Where `/Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/bin/java` points to JDK 1.8.0 on MacOS.
Adjust path depending on your system and desired Java version.

File should look similar to:

```ini
-startup
../Eclipse/plugins/org.eclipse.equinox.launcher_1.4.0.v20161219-1356.jar
--vm
/Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/bin/java
--launcher.library
../Eclipse/plugins/org.eclipse.equinox.launcher.cocoa.macosx.x86_64_1.1.550.v20170928-1359
-product
org.eclipse.epp.package.jee.product
-showsplash
org.eclipse.epp.package.common
--launcher.defaultAction
openFile
--launcher.defaultAction
openFile
--launcher.appendVmargs
-vmargs
-Dosgi.requiredJavaVersion=1.8
-Dosgi.instance.area.default=@user.home/eclipse-workspace
-XX:+UseG1GC
-XX:+UseStringDeduplication
--add-modules=ALL-SYSTEM
-XstartOnFirstThread
-Dorg.eclipse.swt.internal.carbon.smallFonts
-Dosgi.requiredJavaVersion=1.8
-Xms512m
-Xmx5120m
--add-modules=ALL-SYSTEM
-Xdock:icon=../Resources/Eclipse.icns
-XstartOnFirstThread
-Dorg.eclipse.swt.internal.carbon.smallFonts
```
