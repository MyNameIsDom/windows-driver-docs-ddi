---
UID: NF.wdm.KeTestSpinLock
title: KeTestSpinLock function
author: windows-driver-content
description: The KeTestSpinLock routine tests for the availability of a spin lock.
old-location: kernel\ketestspinlock.htm
old-project: kernel
ms.assetid: 5386349c-b4b8-43db-8f66-70dc7e71345e
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: KeTestSpinLock
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Server 2003 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeTestSpinLock
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: See Remarks section.
req.product: Windows 10 or later.
---

# KeTestSpinLock function



## -description
The <b>KeTestSpinLock</b> routine tests for the availability of a spin lock.



## -syntax

````
BOOLEAN KeTestSpinLock(
  _In_ PKSPIN_LOCK SpinLock
);
````


## -parameters

### -param SpinLock [in]

A pointer to a spin lock. The spin lock must have been initialized by calling <a href="kernel.keinitializespinlock">KeInitializeSpinLock</a>.


## -returns
<b>KeTestSpinLock</b> returns <b>FALSE</b> if the spin lock is currently being held. Otherwise, it returns <b>TRUE</b>.


## -remarks
This routine enables the caller that is running at a low IRQL to test the spin lock. If <b>KeTestSpinLock</b> returns <b>TRUE</b>, the caller can try to acquire the spin lock with a high probability of immediate success.

This routine neither raises nor lowers the IRQL, and it never acquires the spin lock.

For more information about spin locks, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563830">Spin Locks</a>.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows Server 2003 and later versions of Windows.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
See Remarks section.

</td>
</tr>
<tr>
<th width="30%">
DDI compliance rules

</th>
<td width="70%">
<a href="devtest.storport_hwstorportprohibitedddis">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.keacquirespinlock">KeAcquireSpinLock</a>
</dt>
<dt>
<a href="kernel.keinitializespinlock">KeInitializeSpinLock</a>
</dt>
<dt>
<a href="kernel.kereleasespinlock">KeReleaseSpinLock</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeTestSpinLock routine%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
