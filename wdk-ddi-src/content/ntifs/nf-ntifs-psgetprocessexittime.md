---
UID: NF:ntifs.PsGetProcessExitTime
title: PsGetProcessExitTime function
author: windows-driver-content
description: The PsGetProcessExitTime routine returns the exit time for the current process.
old-location: ifsk\psgetprocessexittime.htm
old-project: ifsk
ms.assetid: 2d98e2f5-0dc4-4490-a039-eb57f0e5fa87
ms.author: windowsdriverdev
ms.date: 4/16/2018
ms.keywords: PsGetProcessExitTime, PsGetProcessExitTime routine [Installable File System Drivers], ifsk.psgetprocessexittime, ntifs/PsGetProcessExitTime, psref_a3867d14-4a6b-4560-a580-cdc00075b185.xml
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: "<=DISPATCH_LEVEL"
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	DllExport
api_location:
-	NtosKrnl.exe
api_name:
-	PsGetProcessExitTime
product:
- Windows
targetos: Windows
req.typenames: 
---

# PsGetProcessExitTime function


## -description


The <b>PsGetProcessExitTime</b> routine returns the exit time for the current process.


## -parameters








## -returns



<b>PsGetProcessExitTime</b> returns the exit time for the current process, in system time format. 




## -remarks



System time is a count of 100-nanosecond intervals since January 1, 1601. System time is typically updated approximately every ten milliseconds. This value is computed for the GMT time zone. To adjust this value for the local time zone, use <b>ExSystemTimeToLocalTime</b>.

For more information about converting time values, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff542994">Data Conversions</a>. 




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff545622">ExSystemTimeToLocalTime</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff553068">KeQuerySystemTime</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff551915">PsIsThreadTerminating</a>
 

 

