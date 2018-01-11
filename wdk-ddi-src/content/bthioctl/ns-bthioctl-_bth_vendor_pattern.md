---
UID: NS.BTHIOCTL._BTH_VENDOR_PATTERN
title: _BTH_VENDOR_PATTERN
author: windows-driver-content
description: The BTH_VENDOR_PATTERN structure specifies a vendor pattern.
old-location: bltooth\bth_vendor_pattern.htm
old-project: bltooth
ms.assetid: 694020c6-dd0a-46c7-9122-cd86ce28d03a
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _BTH_VENDOR_PATTERN, PBTH_VENDOR_PATTERN, *PBTH_VENDOR_PATTERN, BTH_VENDOR_PATTERN
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: bthioctl.h
req.include-header: Bthioctl.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Available in Windows Vista, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BTH_VENDOR_PATTERN
req.alt-loc: bthioctl.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= PASSIVE_LEVEL
---

# _BTH_VENDOR_PATTERN structure



## -description
The BTH_VENDOR_PATTERN structure specifies a vendor pattern.



## -syntax

````
typedef struct _BTH_VENDOR_PATTERN {
  UCHAR Offset;
  UCHAR Size;
  UCHAR Pattern[1];
} BTH_VENDOR_PATTERN, *PBTH_VENDOR_PATTERN;
````


## -struct-fields

### -field Offset

The offset, in bytes, of the pattern from the beginning of the event data, excluding the event
     header.


### -field Size

The size, in bytes, of the pattern.


### -field Pattern

A buffer that contains pattern data.


## -remarks
The BTH_VENDOR_PATTERN structure specifies vendor patterns for the 
    <a href="bltooth.bth_vendor_specific_command">
    BTH_VENDOR_SPECIFIC_COMMAND</a> structure.

A list of patterns can immediately follow the vendor-specific command data that is specified in the 
    <b>Data</b> member of the BTH_VENDOR_SPECIFIC_COMMAND structure.

Patterns are required if a vendor-specific command does not follow the standard HCI flow control and a
    vendor-specific event is generated in response to the vendor-specific command.


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Versions: Available in Windows Vista, and later versions of Windows.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Bthioctl.h (include Bthioctl.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="bltooth.bth_vendor_specific_command">BTH_VENDOR_SPECIFIC_COMMAND</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20BTH_VENDOR_PATTERN structure%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
