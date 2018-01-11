---
UID: NF.ntifs.RtlOemStringToUnicodeSize
title: RtlOemStringToUnicodeSize macro
author: windows-driver-content
description: The RtlOemStringToUnicodeSize routine determines the size, in bytes, that a given OEM string will be after it is translated into a null-terminated Unicode string.
old-location: ifsk\rtloemstringtounicodesize.htm
old-project: ifsk
ms.assetid: e54d0e3f-4e46-43b5-8338-b6e2f2a14c56
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: RtlOemStringToUnicodeSize
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: macro
req.header: ntifs.h
req.include-header: FltKernel.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlOemStringToUnicodeSize
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
req.irql: < DISPATCH_LEVEL
---

# RtlOemStringToUnicodeSize macro



## -description
The <b>RtlOemStringToUnicodeSize</b> routine determines the size, in bytes, that a given OEM string will be after it is translated into a null-terminated Unicode string. 



## -syntax

````
ULONG RtlOemStringToUnicodeSize(
  _In_ POEM_STRING OemString
);
````


## -parameters

### -param OemString [in]

Pointer to a caller-allocated OEM string. 


## -remarks
<b>RtlOemStringToUnicodeSize</b> can be called to determine how much memory to allocate when translating an OEM string to Unicode with <b>RtlOemStringToUnicodeString</b>. The returned value includes space for the NULL terminator. 

For information about other string-handling routines, see <a href="kernel.strings">Strings</a>. 


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
Header

</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include FltKernel.h or Ntifs.h)</dt>
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
&lt; DISPATCH_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.oem_string">OEM_STRING</a>
</dt>
<dt>
<a href="ifsk.rtloemstringtocountedunicodesize">RtlOemStringToCountedUnicodeSize</a>
</dt>
<dt>
<a href="ifsk.rtloemstringtounicodestring">RtlOemStringToUnicodeString</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlOemStringToUnicodeSize routine%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
