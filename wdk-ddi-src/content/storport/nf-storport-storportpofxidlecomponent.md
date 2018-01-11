---
UID: NF.storport.StorPortPoFxIdleComponent
title: StorPortPoFxIdleComponent function
author: windows-driver-content
description: The StorPortPoFxIdleComponent routine decrements the activation reference count of a specified component of a storage device.
old-location: storage\storportpofxidlecomponent.htm
old-project: storage
ms.assetid: DF329B68-3995-4B38-8208-4C779B0626A6
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: StorPortPoFxIdleComponent
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
req.alt-api: StorPortPoFxIdleComponent
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
req.irql: Any
req.product: Windows 10 or later.
---

# StorPortPoFxIdleComponent function



## -description
The <b>StorPortPoFxIdleComponent</b> routine decrements the activation reference count of a specified component of a storage device.



## -syntax

````
ULONG StorPortPoFxIdleComponent(
  _In_     PVOID               HwDeviceExtension,
  _In_opt_ PSTOR_ADDRESS       Address,
  _In_opt_ PSCSI_REQUEST_BLOCK Srb,
  _In_     ULONG               Component,
  _In_     ULONG               Flags
);
````


## -parameters

### -param HwDeviceExtension [in]

A pointer to the hardware device extension for the host bus adapter (HBA).


### -param Address [in, optional]

The address of a storage device unit. This parameter is <b>NULL</b> when idling a storage adapter component.


### -param Srb [in, optional]

The SRB triggering the component deactivation. This parameter is <b>NULL</b> if the miniport is idling a device component internally.


### -param Component [in]

The index that identifies the component. This parameter is an index into the <b>Components</b> array in the <a href="storage.stor_pofx_device">STOR_POFX_DEVICE</a> structure that the miniport driver registered for the device with a call to <a href="storage.storportinitializepofxpower">StorPortInitializePoFxPower</a>. If the <b>Components</b> array contains N elements, component indexes range from 0 to N–1.


### -param Flags [in]

Not used. Set to 0.


## -returns
The <b>StorPortPoFxIdleComponent</b> routine returns one of these status codes:
<dl>
<dt><b>STOR_STATUS_SUCCESS</b></dt>
</dl>The storage device activation reference was successfully decremented and the component is idle.
<dl>
<dt><b>STOR_STATUS_INVALID_PARAMETER</b></dt>
</dl>Either <i>HwDeviceExtension</i> or <i>Device</i> is NULL.

-or-

<i>Address</i> points to an invalid unit address structure.

-or-

The storage device specified by <i>Address</i> is not found.

-or-

The storage device is  not registered with the power management framework (PoFx).

-or-

The SRB pointed to by <i>Srb</i> is not sent from Storport.

-or-

The <i>Flags</i> parameter is nonzero.
<dl>
<dt><b>STOR_STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl>The adapter or unit does not support PoFx.

-or-

<b>StorPortPoFxIdleComponent</b> was called with an inactive <i>Component</i> and an <i>Srb</i> for which a previous call to   <a href="storage.storportpofxactivatecomponent">StorPortPoFxActivateComponent</a> was not performed.
<dl>
<dt><b>STOR_STATUS_INVALID_IRQL</b></dt>
</dl>The current IRQL &gt; DISPATCH_LEVEL.
<dl>
<dt><b>STOR_STATUS_BUSY</b></dt>
</dl>The active reference for the device component was decremented but the  component is still active.

 


## -remarks
Currently, both adapter devices and unit devices have maximum component count of 1. The index in <i>Component</i> must always be set to 0.

Each call to <b>StorPortPoFxIdleComponent</b> must be matched with a previous call to <a href="storage.storportpofxactivatecomponent">StorPortPoFxActivateComponent</a>.


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
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
Any

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.stor_pofx_device">STOR_POFX_DEVICE</a>
</dt>
<dt>
<a href="storage.storportinitializepofxpower">StorPortInitializePoFxPower</a>
</dt>
<dt>
<a href="storage.storportpofxactivatecomponent">StorPortPoFxActivateComponent</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20StorPortPoFxIdleComponent routine%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
