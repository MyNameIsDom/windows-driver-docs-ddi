---
UID: NS.WDFFDO._WDF_FDO_EVENT_CALLBACKS
title: _WDF_FDO_EVENT_CALLBACKS
author: windows-driver-content
description: The WDF_FDO_EVENT_CALLBACKS structure contains pointers to a function driver's PnP event callback functions.
old-location: wdf\wdf_fdo_event_callbacks.htm
old-project: wdf
ms.assetid: 61e268aa-782a-42d5-8965-b935156033cb
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _WDF_FDO_EVENT_CALLBACKS, PWDF_FDO_EVENT_CALLBACKS, WDF_FDO_EVENT_CALLBACKS, *PWDF_FDO_EVENT_CALLBACKS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wdffdo.h
req.include-header: Wdf.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WDF_FDO_EVENT_CALLBACKS
req.alt-loc: wdffdo.h
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

# _WDF_FDO_EVENT_CALLBACKS structure



## -description
<p class="CCE_Message">[Applies to KMDF only]

The <b>WDF_FDO_EVENT_CALLBACKS</b> structure contains pointers to a function driver's PnP event callback functions.



## -syntax

````
typedef struct _WDF_FDO_EVENT_CALLBACKS {
  ULONG                                       Size;
  PFN_WDF_DEVICE_FILTER_RESOURCE_REQUIREMENTS EvtDeviceFilterAddResourceRequirements;
  PFN_WDF_DEVICE_FILTER_RESOURCE_REQUIREMENTS EvtDeviceFilterRemoveResourceRequirements;
  PFN_WDF_DEVICE_REMOVE_ADDED_RESOURCES       EvtDeviceRemoveAddedResources;
} WDF_FDO_EVENT_CALLBACKS, *PWDF_FDO_EVENT_CALLBACKS;
````


## -struct-fields

### -field Size

The size, in bytes, of this structure.


### -field EvtDeviceFilterAddResourceRequirements

A pointer to the driver's <a href="wdf.evtdevicefilteraddresourcerequirements">EVT_WDF_DEVICE_FILTER_RESOURCE_REQUIREMENTS</a> event callback function, or <b>NULL</b>.


### -field EvtDeviceFilterRemoveResourceRequirements

A pointer to the driver's <a href="wdf.evtdevicefilteraddresourcerequirements">EVT_WDF_DEVICE_FILTER_RESOURCE_REQUIREMENTS</a> event callback function, or <b>NULL</b>.


### -field EvtDeviceRemoveAddedResources

A pointer to the driver's <a href="..\wdffdo\nc-wdffdo-evt_wdf_device_remove_added_resources.md">EvtDeviceRemoveAddedResources</a> event callback function, or <b>NULL</b>.


## -remarks
The <b>WDF_FDO_EVENT_CALLBACKS</b> structure is used as input to the <a href="wdf.wdffdoinitseteventcallbacks">WdfFdoInitSetEventCallbacks</a> method.

Drivers must call <a href="wdf.wdf_fdo_event_callbacks_init">WDF_FDO_EVENT_CALLBACKS_INIT</a> to initialize the structure.

A driver that specifies an <a href="wdf.evtdevicefilteraddresourcerequirements">EvtDeviceFilterAddResourceRequirements</a> event callback function must also specify an <a href="..\wdffdo\nc-wdffdo-evt_wdf_device_remove_added_resources.md">EvtDeviceRemoveAddedResources</a> event callback function.


## -requirements
<table>
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
Header

</th>
<td width="70%">
<dl>
<dt>Wdffdo.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="wdf.wdf_fdo_event_callbacks_init">WDF_FDO_EVENT_CALLBACKS_INIT</a>
</dt>
<dt>
<a href="wdf.wdffdoinitseteventcallbacks">WdfFdoInitSetEventCallbacks</a>
</dt>
<dt>
<a href="wdf.wdf_pdo_event_callbacks">WDF_PDO_EVENT_CALLBACKS</a>
</dt>
<dt>
<a href="wdf.wdfpdoinitseteventcallbacks">WdfPdoInitSetEventCallbacks</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_FDO_EVENT_CALLBACKS structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
