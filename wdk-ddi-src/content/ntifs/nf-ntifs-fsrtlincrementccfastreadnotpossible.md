---
UID: NF.ntifs.FsRtlIncrementCcFastReadNotPossible
title: FsRtlIncrementCcFastReadNotPossible function
author: windows-driver-content
description: The FsRtlIncrementCcFastReadNotPossible routine increments the CcFastReadNotPossible performance counter in a per processor control block of cache manager system counters.
old-location: ifsk\fsrtlincrementccfastreadnotpossible.htm
old-project: ifsk
ms.assetid: 2e0ae5d1-5189-4f78-9729-9c1b9bbf046d
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: FsRtlIncrementCcFastReadNotPossible
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Microsoft Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FsRtlIncrementCcFastReadNotPossible
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level
---

# FsRtlIncrementCcFastReadNotPossible function



## -description
The <b>FsRtlIncrementCcFastReadNotPossible</b> routine increments the CcFastReadNotPossible performance counter in a per processor control block of cache manager system counters.



## -syntax

````
VOID FsRtlIncrementCcFastReadNotPossible(
   VOID 
);
````


## -parameters

### -param  

None


## -returns
This routine does not return a value.


## -remarks
<b>FsRtlIncrementCcFastReadNotPossible </b>increments the CcFastReadNotPossible performance counter in the per processor control block of cache manager system counters. This counter indicates that a fast I/O read operation (<a href="ifsk.fsrtlcopyread">FsRtlCopyRead</a>) was called, but fast I/O was not possible. This counter does not get incremented if fast I/O was not possible because the file resource could not be acquired for shared access. When the resource could not be acquired, the CcFastReadResourceMiss performance counter should be incremented. 

File system drivers should call this function to update the performance counter if the driver chooses to override the default fast I/O read handler.


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
This routine is available on Microsoft Windows XP and later. 

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
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
Any level

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.fsrtlcopyread">FsRtlCopyRead</a>
</dt>
<dt>
<a href="ifsk.fsrtlincrementccfastreadnowait">FsRtlIncrementCcFastReadNoWait</a>
</dt>
<dt>
<a href="ifsk.fsrtlincrementccfastreadresourcemiss">FsRtlIncrementCcFastReadResourceMiss</a>
</dt>
<dt>
<a href="ifsk.fsrtlincrementccfastreadwait">FsRtlIncrementCcFastReadWait</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FsRtlIncrementCcFastReadNotPossible routine%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
