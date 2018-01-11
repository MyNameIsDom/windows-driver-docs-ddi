---
UID: NF.hbaapi.HBA_SetBindingSupport
title: HBA_SetBindingSupport function
author: windows-driver-content
description: The HBA_SetBindingSupport routine enables the indicated set of capabilities on the adapter.
old-location: storage\hba_setbindingsupport.htm
old-project: storage
ms.assetid: 2d4ac375-ede9-406e-bac0-9caa2273c91a
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: HBA_SetBindingSupport
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: hbaapi.h
req.include-header: Hbaapi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HBA_SetBindingSupport
req.alt-loc: Hbaapi.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hbaapi.lib
req.dll: Hbaapi.dll
req.irql: 
---

# HBA_SetBindingSupport function



## -description
The <b>HBA_SetBindingSupport</b> routine enables the indicated set of capabilities on the adapter. 



## -syntax

````
HBA_STATUS HBA_API HBA_SetBindingSupport(
  _In_ HBA_HANDLE          Handle,
  _In_ HBA_WWN             HbaPortWWN,
  _In_ HBA_BIND_CAPABILITY Flags
);
````


## -parameters

### -param Handle [in]

Contains a value returned by the routine <a href="storage.hba_openadapter">HBA_OpenAdapter</a> that identifies the HBA on which the port referenced by <i>HbaPortWWN </i>is located. 


### -param HbaPortWWN [in]

Contains a 64-bit worldwide name (WWN) that uniquely identifies the port for which the binding capabilities specified by <i>Flags </i>are enabled. For a discussion of worldwide names, see the T11 committee's <i>Fibre Channel HBA API</i> specification. 


### -param Flags [in]

Contains a bitwise OR of a set of flags that indicate the capabilities to enable on the port referenced by <i>HbaPortWWN</i>. For a description of the flags, see the corresponding values associated with the <a href="storage.hba_bind_type">HBA_BIND_TYPE</a> WMI property qualifier.


## -returns
The <b>HBA_SetBindingSupport</b> routine returns a value of type <a href="storage.hba_status">HBA_STATUS</a> that indicates the status of the HBA. In particular, <b>HBA_SetBindingSupport</b> returns one of the following values.
<dl>
<dt><b>HBA_STATUS_OK</b></dt>
</dl>Returned if the binding capabilities were successfully enabled. 
<dl>
<dt><b>HBA_STATUS_ERROR_ILLEGAL_WWN</b></dt>
</dl>Returned if the HBA referenced by <i>handle</i> does not contain a port with a name that matches <i>HbaPortWWN</i>. 
<dl>
<dt><b>HBA_STATUS_ERROR_NOT_SUPPORTED</b></dt>
</dl>Returned if the adapter referenced by <i>handle </i>does not support persistent bindings. 
<dl>
<dt><b>HBA_STATUS_ERROR_INCAPABLE</b></dt>
</dl>Returned if one or more of the flags specified by <i>Flags</i> corresponds to a capability not implemented for the port referenced by <i>HbaPortWWN</i>.
<dl>
<dt><b>HBA_STATUS_ERROR</b></dt>
</dl>Returned if an unspecified error occurred that prevented the routine from enabling the specified capabilities. 

 


## -remarks


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
Header

</th>
<td width="70%">
<dl>
<dt>Hbaapi.h (include Hbaapi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Hbaapi.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>Hbaapi.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.hba_openadapter">HBA_OpenAdapter</a>
</dt>
<dt>
<a href="storage.hba_status">HBA_STATUS</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20HBA_SetBindingSupport routine%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
