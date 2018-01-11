---
UID: NI.ks.IOCTL_KS_DISABLE_EVENT
title: IOCTL_KS_DISABLE_EVENT
author: windows-driver-content
description: An application can use IOCTL_KS_DISABLE_EVENT to rescind a previous request notification. The application specifies IOCTL_KS_DISABLE_EVENT in the IoControl parameter of a call to KsSynchronousDeviceControl.
old-location: stream\ioctl_ks_disable_event.htm
old-project: stream
ms.assetid: 4e451d0c-6548-4735-833a-3972cf5e59c6
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _KsEdit
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ks.h
req.include-header: Ks.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_KS_DISABLE_EVENT
req.alt-loc: ks.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
---

# IOCTL_KS_DISABLE_EVENT IOCTL



## -description

An application can use IOCTL_KS_DISABLE_EVENT to rescind a previous request notification. The application specifies IOCTL_KS_DISABLE_EVENT in the <b>IoControl</b> parameter of a call to <a href="stream.kssynchronousdevicecontrol">KsSynchronousDeviceControl</a>.



An application can use IOCTL_KS_DISABLE_EVENT to rescind a previous request notification. The application specifies IOCTL_KS_DISABLE_EVENT in the <b>IoControl</b> parameter of a call to <a href="stream.kssynchronousdevicecontrol">KsSynchronousDeviceControl</a>.



## -ioctlparameters

### -input-buffer
The application places a pointer to a structure of type <a href="..\ks\ns-ks-kseventdata.md">KSEVENTDATA</a> in the <b>InBuffer</b> parameter. This is the location of the original KSEVENTDATA structure that the application instantiated at the enabling of the event. To disable all active events, a client specifies a <b>NULL</b> pointer and length of zero in the <b>InBuffer</b> and <b>InLength</b> parameters.


### -input-buffer-length
Length of <a href="..\ks\ns-ks-kseventdata.md">KSEVENTDATA</a>.


### -output-buffer
None.


### -output-buffer-length
None.


### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
If the request is successful, the Status member is set to STATUS_SUCCESS.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\ks\ns-ks-ksevent_item.md">KSEVENT_ITEM</a>
</dt>
<dt>
<a href="..\ks\ns-ks-ksevent_set.md">KSEVENT_SET</a>
</dt>
<dt>
<a href="stream.ksevent_entry">KSEVENT_ENTRY</a>
</dt>
<dt>
<a href="..\ks\ns-ks-ksdpc_item.md">KSDPC_ITEM</a>
</dt>
<dt>
<a href="..\ks\ns-ks-kseventdata.md">KSEVENTDATA</a>
</dt>
<dt>
<a href="stream.ksevent">KSEVENT</a>
</dt>
<dt>
<a href="stream.ksdisableevent">KsDisableEvent</a>
</dt>
<dt>
<a href="..\ks\ni-ks-ioctl_ks_disable_event.md">IOCTL_KS_DISABLE_EVENT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20IOCTL_KS_DISABLE_EVENT control code%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
