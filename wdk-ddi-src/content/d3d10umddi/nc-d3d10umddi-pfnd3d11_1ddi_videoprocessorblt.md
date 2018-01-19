---
UID : NC:d3d10umddi.PFND3D11_1DDI_VIDEOPROCESSORBLT
title : PFND3D11_1DDI_VIDEOPROCESSORBLT
author : windows-driver-content
description : Performs a video processing operation on one or more input samples and writes the result to a Direct3D surface.
old-location : display\videoprocessorblt.htm
old-project : display
ms.assetid : 7a3e17cb-0397-4051-8443-fb2edf3b4cff
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
req.alt-api : pfnVideoProcessorBlt
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


# PFND3D11_1DDI_VIDEOPROCESSORBLT callback function
Performs a video processing operation on one or more input samples and writes the result to a Direct3D surface.

## Syntax

```
PFND3D11_1DDI_VIDEOPROCESSORBLT Pfnd3d111DdiVideoprocessorblt;

HRESULT Pfnd3d111DdiVideoprocessorblt(
   D3D10DDI_HDEVICE,
   D3D11_1DDI_HVIDEOPROCESSOR,
   D3D11_1DDI_HVIDEOPROCESSOROUTPUTVIEW,
   UINT,
   UINT,
  CONST D3D11_1DDI_VIDEO_PROCESSOR_STREAM *
)
{...}
```

## Parameters

`D3D10DDI_HDEVICE`



`D3D11_1DDI_HVIDEOPROCESSOR`



`D3D11_1DDI_HVIDEOPROCESSOROUTPUTVIEW`



`UINT`



`UINT`



`*`




## Return Value

<b>VideoProcessorBlt</b> returns one of the following values:
<dl>
<dt><b>S_OK</b></dt>
</dl>The video processing operation completed successfully.
<dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl>
        Memory was not available to complete the operation.

## Remarks

The <b>VideoProcessorBlt</b> performs all of the video processing based on the stream states and bit-block transfer (bitblt) states that have been previously set.

The Microsoft Direct3D runtime performs the following data validation before it calls the driver's <b>VideoProcessorBlt</b> function:

The input and output <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> structures may be adjusted if the rectangles are not aligned properly according to the requirements of the format.


If the video processor has been enabled to produce stereo samples, the output view must contain a texture array of two elements.
Also, at least one stereo stream must be specified.

If the video processor has been disabled from producing stereo samples, the output view must contain a single element.
 Also, the stereo format cannot be configured as <b>D3D11_VIDEO_PROCESSOR_STEREO_FORMAT_MONO</b>.


Each input stream is specified through a 	<a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_processor_stream.md">D3D11_1DDI_VIDEO_PROCESSOR_STREAM</a> structure. If the stereo format of the input stream is configured to be <b>D3D11_1DDI_VIDEO_PROCESSOR_STEREO_FORMAT_SEPARATE</b>, the <b>pInputSurfaceRight</b> member must not be set to NULL.  Otherwise, the <b>pInputSurfaceRight</b> must be set to NULL.



If multiple input streams are enabled and the video processor is enabled to produce stereo output, it is possible that one of the input streams may be a mono sample.

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
<a href="..\d3d10umddi\nc-d3d10umddi-pfnd3d11_1ddi_createvideoprocessor.md">CreateVideoProcessor</a>
</dt>
<dt><b>CreateVideoProcessorOutputView</b></dt>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_processor_caps.md">D3D11_1DDI_VIDEO_PROCESSOR_CAPS</a>
</dt>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d11_1ddi_video_processor_stream.md">D3D11_1DDI_VIDEO_PROCESSOR_STREAM</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a>
</dt>
<dt>
<a href="..\d3d10umddi\nc-d3d10umddi-pfnd3d11_1ddi_videoprocessorsetoutputstereomode.md">VideoProcessorSetOutputStereoMode</a>
</dt>
<dt>
<a href="..\d3d10umddi\nc-d3d10umddi-pfnd3d11_1ddi_videoprocessorsetstreamstereoformat.md">VideoProcessorSetStreamStereoFormat</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D11_1DDI_VIDEOPROCESSORBLT callback function%20 RELEASE:%20(12/29/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>