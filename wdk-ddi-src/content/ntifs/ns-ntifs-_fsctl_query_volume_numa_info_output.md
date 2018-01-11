---
UID: NS.NTIFS._FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT
title: _FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT
author: windows-driver-content
description: The FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT structure specifies the Non-Uniform Memory Architecture (NUMA) node the volume resides on.
old-location: ifsk\fsctl_query_volume_numa_info_output_.htm
old-project: ifsk
ms.assetid: 3BB6F409-A716-4990-B1C6-D0F8035DA7F0
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT, PFSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT, *PFSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT, FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: ntifs.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT
req.alt-loc: Ntifs.h
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

# _FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT structure



## -description
The <b>FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT</b> structure specifies the Non-Uniform Memory Architecture (NUMA) node the volume resides on.



## -syntax

````
typedef struct _FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT  {
  ULONG NumaNode;
} FSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT , *PFSCTL_QUERY_VOLUME_NUMA_INFO_OUTPUT ;
````


## -struct-fields

### -field NumaNode

Specifies the number of the NUMA node the volume resides on.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntifs.h</dt>
</dl>
</td>
</tr>
</table>