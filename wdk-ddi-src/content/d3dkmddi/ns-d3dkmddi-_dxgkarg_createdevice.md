---
UID: NS.D3DKMDDI._DXGKARG_CREATEDEVICE
title: _DXGKARG_CREATEDEVICE
author: windows-driver-content
description: The DXGKARG_CREATEDEVICE structure describes a graphics context device.
old-location: display\dxgkarg_createdevice.htm
old-project: display
ms.assetid: 88d20349-4039-4a5d-a1fd-0488148c623d
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _DXGKARG_CREATEDEVICE, DXGKARG_CREATEDEVICE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGKARG_CREATEDEVICE
req.alt-loc: d3dkmddi.h
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
---

# _DXGKARG_CREATEDEVICE structure



## -description
The DXGKARG_CREATEDEVICE structure describes a graphics context device.



## -syntax

````
typedef struct _DXGKARG_CREATEDEVICE {
  HANDLE hDevice;
  union {
    DXGK_CREATEDEVICEFLAGS Flags;
    DXGK_DEVICEINFO        *pInfo;
  };
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM2_0)
  ULONG  Pasid;
  HANDLE hKmdProcess;
#endif 
} DXGKARG_CREATEDEVICE;
````


## -struct-fields

### -field hDevice

A handle to the graphics context device. On input to the <a href="..\d3dkmddi\nc-d3dkmddi-dxgkddi_createdevice.md">DxgkDdiCreateDevice</a> function, <b>hDevice</b> specifies the handle that the driver should use when it calls back into the Microsoft DirectX graphics kernel subsystem. 

The driver generates a unique handle and passes it back to the DirectX graphics subsystem. On output from the <a href="..\d3dkmddi\nc-d3dkmddi-dxgkddi_createdevice.md">DxgkDdiCreateDevice</a> function, <b>hDevice</b> specifies the handle that the DirectX graphics subsystem should use in subsequent driver calls to identify the device.


### -field Flags

 A <a href="display.dxgk_createdeviceflags">DXGK_CREATEDEVICEFLAGS</a> structure that identifies how to create the device.


### -field pInfo

A pointer to a <a href="display.dxgk_deviceinfo">DXGK_DEVICEINFO</a> structure that contains parameters that the DirectX graphics subsystem requires from the display miniport driver.


### -field Pasid

The owner process PASID for a support vector machine GPU.

Supported starting with Windows 10.


### -field hKmdProcess

A handle to the corresponding kernel mode driver process object.

Supported starting with Windows 10.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows Vista and later versions of the Windows operating systems.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="display.dxgk_createdeviceflags">DXGK_CREATEDEVICEFLAGS</a>
</dt>
<dt>
<a href="display.dxgk_deviceinfo">DXGK_DEVICEINFO</a>
</dt>
<dt>
<a href="..\d3dkmddi\nc-d3dkmddi-dxgkddi_createdevice.md">DxgkDdiCreateDevice</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_CREATEDEVICE structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
