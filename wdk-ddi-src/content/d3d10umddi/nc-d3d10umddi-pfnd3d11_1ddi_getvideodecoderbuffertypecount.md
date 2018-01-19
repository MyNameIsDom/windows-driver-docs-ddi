---
UID : NC:d3d10umddi.PFND3D11_1DDI_GETVIDEODECODERBUFFERTYPECOUNT
title : PFND3D11_1DDI_GETVIDEODECODERBUFFERTYPECOUNT
author : windows-driver-content
description : Queries the number of buffer types that the display miniport driver requires to perform a specified decode operation.
old-location : display\getvideodecoderbuffertypecount.htm
old-project : display
ms.assetid : 3528ac03-55cf-4e02-ae42-69b736684147
ms.author : windowsdriverdev
ms.date : 12/29/2017
ms.keywords : _SETRESULT_INFO, *PSETRESULT_INFO, SETRESULT_INFO
ms.prod : windows-hardware
ms.technology : windows-devices
ms.topic : callback
req.header : d3d10umddi.h
req.include-header : D3d10umddi.h
req.target-type : Desktop
req.target-min-winverclnt : Windows 8
req.target-min-winversvr : Windows Server 2012
req.kmdf-ver : 
req.umdf-ver : 
req.alt-api : pfnGetVideoDecoderBufferTypeCount
req.alt-loc : D3d10umddi.h
req.ddi-compliance : 
req.unicode-ansi : 
req.idl : 
req.max-support : 
req.namespace : 
req.assembly : 
req.type-library : 
req.lib : 
req.dll : 
req.irql : 
req.typenames : "*PSETRESULT_INFO, SETRESULT_INFO"
---


# PFND3D11_1DDI_GETVIDEODECODERBUFFERTYPECOUNT callback function
Queries the number of buffer types that the display miniport driver requires to perform a specified decode operation.

## Syntax

```
PFND3D11_1DDI_GETVIDEODECODERBUFFERTYPECOUNT Pfnd3d111DdiGetvideodecoderbuffertypecount;

void Pfnd3d111DdiGetvideodecoderbuffertypecount(
   D3D10DDI_HDEVICE,
  CONST D3D11_1DDI_VIDEO_DECODER_DESC *,
  UINT *
)
{...}
```

## Parameters

`D3D10DDI_HDEVICE`



`*`



`*`




## Return Value

This callback function does not return a value.

## Remarks

The Microsoft Direct3D runtime verifies that the <i>pDecodeDesc</i>  parameter data is valid before it calls the <b>GetVideoDecoderBufferTypeCount</b> function.

## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows Driver kit version** |  |
| **Target platform** | Desktop |
| **Minimum KMDF version** |  |
| **Minimum UMDF version** |  |
| **Header** | d3d10umddi.h (include D3d10umddi.h) |
| **Library** |  |
| **IRQL** |  |
| **DDI compliance rules** |  |

## See Also

<dl>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_decoder_desc.md">D3D11_1DDI_VIDEO_DECODER_DESC</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D11_1DDI_GETVIDEODECODERBUFFERTYPECOUNT callback function%20 RELEASE:%20(12/29/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>