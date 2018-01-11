---
UID: NS.NDISWWAN._NDIS_WWAN_SMS_SEND
title: _NDIS_WWAN_SMS_SEND
author: windows-driver-content
description: The NDIS_WWAN_SMS_SEND structure represents an SMS message to send.
old-location: netvista\ndis_wwan_sms_send.htm
old-project: NetVista
ms.assetid: d92c0ebe-4a11-49d9-95aa-182e99ca8dcf
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _NDIS_WWAN_SMS_SEND, PNDIS_WWAN_SMS_SEND, NDIS_WWAN_SMS_SEND, *PNDIS_WWAN_SMS_SEND
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ndiswwan.h
req.include-header: Ndiswwan.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_WWAN_SMS_SEND
req.alt-loc: ndiswwan.h
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

# _NDIS_WWAN_SMS_SEND structure



## -description
The NDIS_WWAN_SMS_SEND structure represents an SMS message to send.



## -syntax

````
typedef struct _NDIS_WWAN_SMS_SEND {
  NDIS_OBJECT_HEADER Header;
  WWAN_SMS_SEND      SmsSend;
} NDIS_WWAN_SMS_SEND, *PNDIS_WWAN_SMS_SEND;
````


## -struct-fields

### -field Header

The header with type, revision, and size information about the NDIS_WWAN_SMS_SEND structure. The
     MB Service sets the header with the values that are shown in the following table when it sends the data
     structure to the miniport driver for 
     <i>set</i> operations. Miniport drivers must set the header with the same values when they send the data
     structure to the MB service.
     

<table>
<tr>
<th>Header submember</th>
<th>Value</th>
</tr>
<tr>
<td>
Type

</td>
<td>
NDIS_OBJECT_TYPE_DEFAULT

</td>
</tr>
<tr>
<td>
Revision

</td>
<td>
NDIS_WWAN_SMS_SEND_REVISION_1

</td>
</tr>
<tr>
<td>
Size

</td>
<td>
sizeof(NDIS_WWAN_SMS_SEND)

</td>
</tr>
</table>
 

For more information about these members, see 
     <a href="netvista.ndis_object_header">NDIS_OBJECT_HEADER</a>.


### -field SmsSend

A formatted 
     <a href="netvista.wwan_sms_send">WWAN_SMS_SEND</a> object that represents a SMS
     text message to send.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows 7 and later versions of Windows.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ndiswwan.h (include Ndiswwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="netvista.ndis_object_header">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="netvista.wwan_sms_send">WWAN_SMS_SEND</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [NetVista\netvista]:%20NDIS_WWAN_SMS_SEND structure%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
