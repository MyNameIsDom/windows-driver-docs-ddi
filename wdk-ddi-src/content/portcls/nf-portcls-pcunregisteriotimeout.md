---
UID: NF.portcls.PcUnregisterIoTimeout
title: PcUnregisterIoTimeout function
author: windows-driver-content
description: The PcUnregisterIoTimeout function unregisters a driver-supplied I/O-timer callback routine for a specified device object.
old-location: audio\pcunregisteriotimeout.htm
old-project: audio
ms.assetid: 4266c775-a2e9-46f0-91ad-6f6cce06bea0
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: PcUnregisterIoTimeout
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: portcls.h
req.include-header: Portcls.h
req.target-type: Universal
req.target-min-winverclnt: The PortCls system driver implements the PcUnregisterIoTimeout function in Microsoft Windows 98/Me and in Windows 2000 and later operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcUnregisterIoTimeout
req.alt-loc: Portcls.lib,Portcls.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Portcls.lib
req.dll: 
req.irql: PASSIVE_LEVEL
---

# PcUnregisterIoTimeout function



## -description
The <b>PcUnregisterIoTimeout</b> function unregisters a driver-supplied I/O-timer callback routine for a specified device object.



## -syntax

````
NTSTATUS PcUnregisterIoTimeout(
  _In_ PDEVICE_OBJECT    pDeviceObject,
  _In_ PIO_TIMER_ROUTINE pTimerRoutine,
  _In_ PVOID             pContext
);
````


## -parameters

### -param pDeviceObject [in]

Pointer to the same device object that the driver supplied when it previously called <a href="audio.pcregisteriotimeout">PcRegisterIoTimeout</a>. The device object is a system structure of type <a href="kernel.device_object">DEVICE_OBJECT</a>.


### -param pTimerRoutine [in]

Pointer to the same I/O-timer callback routine that the driver supplied when it previously called <a href="audio.pcregisteriotimeout">PcRegisterIoTimeout</a>



### -param pContext [in]

Pointer to the same driver-determined context that the driver supplied when it previously called <a href="audio.pcregisteriotimeout">PcRegisterIoTimeout</a>



## -returns
<b>PcUnregisterIoTimeout</b> returns STATUS_SUCCESS if the call was successful. Otherwise, it returns an appropriate error code. The following table shows some of the possible error codes.
<dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl>Indicates that no timer callback with the same device object, callback routine, and context is currently registered.

 


## -remarks
This call succeeds only if a time-out callback with the same device object, timer routine, and context was previously registered with a call to the <a href="audio.pcregisteriotimeout">PcRegisterIoTimeout</a> function.


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
The PortCls system driver implements the PcUnregisterIoTimeout function in Microsoft Windows 98/Me and in Windows 2000 and later operating systems.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Portcls.h (include Portcls.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Portcls.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
PASSIVE_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="audio.pcregisteriotimeout">PcRegisterIoTimeout</a>
</dt>
<dt>
<a href="kernel.device_object">DEVICE_OBJECT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PcUnregisterIoTimeout function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
