---
UID: NS.NTDDRILAPITYPES.RILIMSFAILURE
title: RILIMSFAILURE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilimsfailure.htm
old-project: NetVista
ms.assetid: 8be10470-3761-4120-8987-00d6fcc9a989
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: RILIMSFAILURE, RILIMSFAILURE, LPRILIMSFAILURE, *LPRILIMSFAILURE
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ntddrilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILIMSFAILURE
req.alt-loc: ntddrilapitypes.h
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
---

# RILIMSFAILURE structure



## -description
This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.



## -syntax

````
typedef struct _RILIMSFAILURE {
  DWORD                     cbSize;
  DWORD                     dwParams;
  DWORD                     dwExecutor;
  RILIMSFAILUREMESSAGETYPE  dwMessageType;
  DWORD                     dwMessageSubType;
  DWORD                     dwErrorCode;
  WCHAR [256]               wszErrorString;
} RILIMSFAILURE, RILIMSFAILURE;
````


## -struct-fields

### -field cbSize


### -field dwParams


### -field dwExecutor


### -field dwMessageType


### -field dwMessageSubType


### -field dwErrorCode


### -field wszErrorString


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntddrilapitypes.h</dt>
</dl>
</td>
</tr>
</table>