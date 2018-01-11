---
UID: NS.USBFNATTACH._USBFN_INTERFACE_ATTACH
title: _USBFN_INTERFACE_ATTACH
author: windows-driver-content
description: Stores pointers to driver-implemented callback functions for handling attach and detach operations.
old-location: buses\usbfn_interface_attach.htm
old-project: UsbRef
ms.assetid: C7D7935C-0536-43E6-8924-1DC13B258007
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _USBFN_INTERFACE_ATTACH, PUSBFN_INTERFACE_ATTACH, USBFN_INTERFACE_ATTACH, *PUSBFN_INTERFACE_ATTACH
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: usbfnattach.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: USBFN_INTERFACE_ATTACH
req.alt-loc: usbfnattach.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# _USBFN_INTERFACE_ATTACH structure



## -description
Stores pointers to driver-implemented callback functions for handling attach and detach operations.



## -syntax

````
typedef struct _USBFN_INTERFACE_ATTACH {
  INTERFACE                   InterfaceHeader;
  PFN_USBFN_GET_ATTACH_ACTION GetAttachAction;
  PFN_USBFN_GET_ATTACH_ACTION GetAttachActionAbortOperation;
  PFN_USBFN_SET_DEVICE_STATE  SetDeviceState;
} USBFN_INTERFACE_ATTACH, *PUSBFN_INTERFACE_ATTACH;
````


## -struct-fields

### -field InterfaceHeader

The interface version number.


### -field GetAttachAction

A pointer to the driver's implementation of the <a href="..\usbfnattach\nc-usbfnattach-usbfn_get_attach_action.md">USBFN_GET_ATTACH_ACTION</a> callback function.


### -field GetAttachActionAbortOperation

A pointer to the driver's implementation of the <a href="..\usbfnattach\nc-usbfnattach-usbfn_get_attach_action_abort.md">USBFN_GET_ATTACH_ACTION_ABORT</a> callback function.


### -field SetDeviceState

A pointer to the driver's implementation of the <a href="..\usbfnattach\nc-usbfnattach-usbfn_set_device_state.md">USBFN_SET_DEVICE_STATE</a> callback function.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Usbfnattach.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses.usb_filter_driver_for_proprietary_charging">USB filter driver for supporting proprietary chargers</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [UsbRef\buses]:%20USBFN_INTERFACE_ATTACH structure%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
