---
UID: NS.RILAPITYPES.RILMSGMWIDETAILLIST
title: RILMSGMWIDETAILLIST
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilmsgmwidetaillist_2.htm
old-project: NetVista
ms.assetid: dbaae4cd-3d0e-4130-af03-9f30a7cd6139
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: RILMSGMWIDETAILLIST, *LPRILMSGMWIDETAILLIST, RILMSGMWIDETAILLIST
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILMSGMWIDETAILLIST
req.alt-loc: rilapitypes.h
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

# RILMSGMWIDETAILLIST structure



## -description
This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. 



## -syntax

````
typedef struct _RILMSGMWIDETAILLIST {
  DWORD               cbSize;
  DWORD               dwParams;
  DWORD               dwExecutor;
  DWORD               dwReferenceNumber;
  DWORD               dwNumberOfDetailItems;
  RILMSGMWIDETAIL [1] stMwiDetail;
} RILMSGMWIDETAILLIST, RILMSGMWIDETAILLIST;
````


## -struct-fields

### -field cbSize


### -field dwParams


### -field dwExecutor


### -field dwReferenceNumber


### -field dwNumberOfDetailItems


### -field stMwiDetail


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Rilapitypes.h</dt>
</dl>
</td>
</tr>
</table>