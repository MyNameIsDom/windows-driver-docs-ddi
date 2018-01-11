---
UID: NS.D3DKMDDI._DXGK_QUERYSEGMENTIN4
title: _DXGK_QUERYSEGMENTIN4
author: windows-driver-content
description: The DXGK_QUERYSEGMENTIN4 structure is used to specify the adapter to query.
old-location: display\dxgk_querysegmentin4.htm
old-project: display
ms.assetid: B78E5AEF-DC31-44B2-92D8-DE7C83726E29
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _DXGK_QUERYSEGMENTIN4, DXGK_QUERYSEGMENTIN4
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_QUERYSEGMENTIN4
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

# _DXGK_QUERYSEGMENTIN4 structure



## -description
The <b>DXGK_QUERYSEGMENTIN4</b> structure is used to specify the adapter to query.



## -syntax

````
typedef struct _DXGK_QUERYSEGMENTIN4 {
  UINT PhysicalAdapterIndex;
} DXGK_QUERYSEGMENTIN4;
````


## -struct-fields

### -field PhysicalAdapterIndex

A zero-based physical adapter index in a linked display adapter  (LDA) link. Zero for non-LDA configurations. 


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 10

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2016

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
<a href="display.dxgk_querysegmentout4">DXGK_QUERYSEGMENTOUT4</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGK_QUERYSEGMENTIN4 structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
