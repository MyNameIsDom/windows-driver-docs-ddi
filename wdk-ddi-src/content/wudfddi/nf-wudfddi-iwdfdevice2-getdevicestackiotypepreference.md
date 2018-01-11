---
UID: NF.wudfddi.IWDFDevice2.GetDeviceStackIoTypePreference
title: IWDFDevice2::GetDeviceStackIoTypePreference method
author: windows-driver-content
description: The GetDeviceStackIoTypePreference method retrieves the buffer access methods that the framework is using for a device.
old-location: wdf\iwdfdevice2_getdevicestackiotypepreference.htm
old-project: wdf
ms.assetid: 3a1f6432-3f61-4502-ac98-fa984539f88e
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: IWDFDevice2, IWDFDevice2::GetDeviceStackIoTypePreference, GetDeviceStackIoTypePreference
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: wudfddi.h
req.include-header: Wudfddi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.9
req.alt-api: IWDFDevice2.GetDeviceStackIoTypePreference
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: 
req.product: Windows 10 or later.
---

# IWDFDevice2::GetDeviceStackIoTypePreference method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]

The <b>GetDeviceStackIoTypePreference</b> method retrieves the buffer access methods that the framework is using for a device.



## -syntax

````
void GetDeviceStackIoTypePreference(
  [out] WDF_DEVICE_IO_TYPE *ReadWritePreference,
  [out] WDF_DEVICE_IO_TYPE *IoControlPreference
);
````


## -parameters

### -param ReadWritePreference [out]

A pointer to a driver-allocated location that receives a <a href="wdf.wdf_device_io_type__umdf_">WDF_DEVICE_IO_TYPE</a>-typed value. This value identifies the buffer access method that the framework is using for a device's read and write requests.


### -param IoControlPreference [out]

A pointer to a driver-allocated location that receives a <a href="wdf.wdf_device_io_type__umdf_">WDF_DEVICE_IO_TYPE</a>-typed value. This value that identifies the buffer access method that the framework is using for a device's I/O control requests.


## -returns
None.


## -remarks
If your driver calls <b>GetDeviceStackIoTypePreference</b> before the PnP manager has loaded all of the device's drivers, the values that <b>GetDeviceStackIoTypePreference</b> retrieves might not be the values that it actually uses.

For more information about how the framework chooses a buffer access method, see <a href="wdf.accessing_data_buffers_in_umdf_drivers#how_umdf_chooses_a_buffer_access_method_for_an_i_o_request#how_umdf_chooses_a_buffer_access_method_for_an_i_o_request">How UMDF Chooses a Buffer Access Method for an I/O Request</a>.

The following code example retrieves the buffer access methods that the framework is using for a device.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
End of support

</th>
<td width="70%">
Unavailable in UMDF 2.0 and later.

</td>
</tr>
<tr>
<th width="30%">
Minimum UMDF version

</th>
<td width="70%">
1.9

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wudfddi.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\wudfddi\nn-wudfddi-iwdfdevice2.md">IWDFDevice2</a>
</dt>
<dt>
<a href="wdf.iwdfdeviceinitialize2_setiotypepreference">IWDFDeviceInitialize2::SetIoTypePreference</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFDevice2::GetDeviceStackIoTypePreference method%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
