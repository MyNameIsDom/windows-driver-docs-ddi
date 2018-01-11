---
UID: NS.D3D12UMDDI.D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032
title: D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032
author: windows-driver-content
description: Video decode bitstream encryption scheme count data.
old-location: display\d3d12ddi-video-decode-bitstream-encryption-scheme-count-data-0032.htm
old-project: display
ms.assetid: 0aba733b-a69a-4a8a-a8bc-e934fbbbacbf
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032, D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3d12umddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032
req.alt-loc: d3d12umddi.h
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

# D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032 structure



## -description
Video decode bitstream encryption scheme count data.



## -syntax

````
typedef struct _D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032 {
  UINT  NodeIndex;
  GUID  DecodeProfile;
  UINT  BitstreamEncryptionSchemeCount;
} D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032, D3D12DDI_VIDEO_DECODE_BITSTREAM_ENCRYPTION_SCHEME_COUNT_DATA_0032;
````


## -struct-fields

### -field NodeIndex

Node index.


### -field DecodeProfile

Decode profile.


### -field BitstreamEncryptionSchemeCount

Bitstream encryption scheme count.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>D3d12umddi.h</dt>
</dl>
</td>
</tr>
</table>