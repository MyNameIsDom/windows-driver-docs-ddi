---
UID: NF.ucxusbdevice.UcxUsbDeviceInitSetEventCallbacks
title: UcxUsbDeviceInitSetEventCallbacks function
author: windows-driver-content
description: Initializes a UCXUSBDEVICE_INIT structure with client driver's event callback functions.
old-location: buses\_ucxusbdeviceinitseteventcallbacks.htm
old-project: UsbRef
ms.assetid: 913F96FD-9C51-4A45-86A9-8830E1A395EE
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: UcxUsbDeviceInitSetEventCallbacks
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ucxusbdevice.h
req.include-header: Ucxclass.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: UcxUsbDeviceInitSetEventCallbacks
req.alt-loc: ucxusbdevice.h
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
req.product: Windows 10 or later.
---

# UcxUsbDeviceInitSetEventCallbacks function



## -description
Initializes a <b>UCXUSBDEVICE_INIT</b> structure with client driver's event callback functions.



## -syntax

````
inline void UcxUsbDeviceInitSetEventCallbacks(
  [in, out] PUCXUSBDEVICE_INIT             UsbDeviceInit,
  [in]      PUCX_USBDEVICE_EVENT_CALLBACKS EventCallbacks
);
````


## -parameters

### -param UsbDeviceInit [in, out]

A pointer to a <b>UCXUSBDEVICE_INIT</b> structure that UCX passes when it invokes client driver's <a href="..\ucxcontroller\nc-ucxcontroller-evt_ucx_controller_usbdevice_add.md">EVT_UCX_CONTROLLER_USBDEVICE_ADD</a> 		event callback function. 


### -param EventCallbacks [in]

A pointer to a <a href="buses._ucx_usbdevice_event_callbacks">UCX_USBDEVICE_EVENT_CALLBACKS</a> structure that contains function pointer to client driver's event callback functions. The  the client driver initializes the structure  by calling <a href="buses._ucx_usbdevice_event_callbacks_init">UCX_USBDEVICE_EVENT_CALLBACKS_INIT</a>.


## -returns
This method does not return a value.


## -remarks
An initialized <b>UCXUSBDEVICE_INIT</b> structure is used by the <a href="buses._ucxusbdevicecreate">UcxUsbDeviceCreate</a> method to create a USB device and register the client driver's event callback functions. 

For a code example, see <a href="..\ucxcontroller\nc-ucxcontroller-evt_ucx_controller_usbdevice_add.md">EVT_UCX_CONTROLLER_USBDEVICE_ADD</a>.


## -requirements
<table>
<tr>
<th width="30%">
Minimum support

</th>
<td width="70%">
Windows 10

</td>
</tr>
<tr>
<th width="30%">
Minimum KMDF version

</th>
<td width="70%">
1.0

</td>
</tr>
<tr>
<th width="30%">
Minimum UMDF version

</th>
<td width="70%">
2.0

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ucxusbdevice.h (include Ucxclass.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses._ucx_usbdevice_event_callbacks">UCX_USBDEVICE_EVENT_CALLBACKS</a>
</dt>
<dt>
<a href="buses._ucxusbdevicecreate">UcxUsbDeviceCreate</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [UsbRef\buses]:%20UcxUsbDeviceInitSetEventCallbacks method%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
