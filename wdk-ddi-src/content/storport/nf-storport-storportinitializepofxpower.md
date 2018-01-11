---
UID: NF.storport.StorPortInitializePoFxPower
title: StorPortInitializePoFxPower function
author: windows-driver-content
description: A miniport driver calls StorPortInitializePoFxPower to register a storage device with the power management framework (PoFx).
old-location: storage\storportinitializepofxpower.htm
old-project: storage
ms.assetid: 154EAF9B-4B30-4124-B31D-6C7D09B52674
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: StorPortInitializePoFxPower
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: storport.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Available in starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortInitializePoFxPower
req.alt-loc: storport.h
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

# StorPortInitializePoFxPower function



## -description
A miniport driver calls <b>StorPortInitializePoFxPower</b> to register a storage device with the power management framework (PoFx).



## -syntax

````
ULONG StorPortInitializePoFxPower(
  _In_     PVOID             HwDeviceExtension,
  _In_opt_ PSTOR_ADDRESS     Address,
  _In_     PSTOR_POFX_DEVICE Device,
  _Inout_  PBOOLEAN          D3ColdEnabled
);
````


## -parameters

### -param HwDeviceExtension [in]

A pointer to the hardware device extension for the host bus adapter (HBA).


### -param Address [in, optional]

The address of a storage device unit. This parameter is <b>NULL</b> when registering for a storage adapter.


### -param Device [in]

A pointer to a <b>STOR_POFX_DEVICE_V2</b> structure cast to a pointer to <a href="storage.stor_pofx_device">STOR_POFX_DEVICE</a>. This structure contains a component list with F-states for a storage device.


### -param D3ColdEnabled [in, out]

A pointer to a <b>BOOLEAN</b> value which the Storport driver will set to indicate whether the D3 Cold state is enabled for the storage device.


## -returns
The <b>StorPortInitializePoFxPower</b> routine returns one of these status codes:
<dl>
<dt><b>STOR_STATUS_INVALID_PARAMETER</b></dt>
</dl>Either <i>HwDeviceExtension</i> or <i>Device</i> is NULL.

-or-

<i>Address</i> points to an invalid unit address structure.

-or-

The storage device specified by <i>Address</i> is not found.

-or-

The <a href="storage.stor_pofx_device">STOR_POFX_DEVICE</a> structure pointed to by  <i>Device</i> is formatted incorrectly or contains invalid data.
<dl>
<dt><b>STOR_STATUS_SUCCESS</b></dt>
</dl>The storage device was successfully registered with PoFx.
<dl>
<dt><b>STOR_STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>Sufficient resources are not available to register the storage device with PoFx.
<dl>
<dt><b>STOR_STATUS_UNSUCCESSFUL</b></dt>
</dl>The storage device was not successfully registered with PoFx.

-or-

The storage device is already registered with PoFx.

 


## -remarks
Adapter devices are always registered with a <b>NULL</b> value for <i>address</i>. Unit devices are registered by specifying a valid unit address for <i>address</i>.

If the <b>STOR_POFX_DEVICE_FLAG_ENABLE_D3_COLD</b> flag is set in the <b>Flags</b> member of <i>Device</i>, Storport will attempt to enable D3 Cold support for the device component. The D3 Cold enabled status is returned in the <b>BOOLEAN</b> value pointed to by <i>D3ColdEnabled</i>.


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
Available in starting with Windows 8.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Storport.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.stor_pofx_device">STOR_POFX_DEVICE</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20StorPortInitializePoFxPower routine%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
