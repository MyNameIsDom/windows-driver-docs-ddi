---
UID: NE.d3dkmdt._D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY
title: _D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY
author: windows-driver-content
description: Specifies the capabilities for the preemption of graphic processing unit (GPU) graphics operations that the display miniport driver supports.
old-location: display\d3dkmdt_graphics_preemption_granularity.htm
old-project: display
ms.assetid: 589b0eac-235a-4403-a917-ae3241313c8e
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY, D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: enum
req.header: d3dkmdt.h
req.include-header: D3dkmdt.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY
req.alt-loc: D3dkmdt.h
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

# _D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY enumeration



## -description
Specifies the capabilities for the preemption of graphic processing unit (GPU) graphics operations that the display miniport driver supports.



## -syntax

````
typedef enum _D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY { 
  D3DKMDT_GRAPHICS_PREEMPTION_NONE                 = 0,
  D3DKMDT_GRAPHICS_PREEMPTION_DMA_BUFFER_BOUNDARY  = 100,
  D3DKMDT_GRAPHICS_PREEMPTION_PRIMITIVE_BOUNDARY   = 200,
  D3DKMDT_GRAPHICS_PREEMPTION_TRIANGLE_BOUNDARY    = 300,
  D3DKMDT_GRAPHICS_PREEMPTION_PIXEL_BOUNDARY       = 400,
  D3DKMDT_GRAPHICS_PREEMPTION_SHADER_BOUNDARY      = 500
} D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY;
````


## -enum-fields

### -field D3DKMDT_GRAPHICS_PREEMPTION_NONE

The driver does not support the preemption of GPU graphics operations.

<div class="alert"><b>Note</b>  This value also specifies that the driver cannot stop currently running DMA buffers of a specified type and cannot prevent all pending DMA buffers in the hardware queue from running.</div>
<div> </div>

### -field D3DKMDT_GRAPHICS_PREEMPTION_DMA_BUFFER_BOUNDARY

The driver cannot stop currently running DMA buffers of a specified type but can prevent all pending DMA buffers in the hardware queue from running.


### -field D3DKMDT_GRAPHICS_PREEMPTION_PRIMITIVE_BOUNDARY

The driver cannot stop currently running primitive buffers of a specified type but can prevent all pending primitive buffers in the hardware queue from running.


### -field D3DKMDT_GRAPHICS_PREEMPTION_TRIANGLE_BOUNDARY

The driver cannot stop currently running triangle buffers of a specified type but can prevent all pending triangle buffers in the hardware queue from running.


### -field D3DKMDT_GRAPHICS_PREEMPTION_PIXEL_BOUNDARY

The driver cannot stop currently running pixel buffers of a specified type but can prevent all pending pixel buffers in the hardware queue from running.


### -field D3DKMDT_GRAPHICS_PREEMPTION_SHADER_BOUNDARY

The driver cannot stop currently running shader instruction buffers of a specified type but can prevent all pending shader instruction buffers in the hardware queue from running.


## -remarks
Starting with Windows 8, display miniport drivers need to specify the level of preemption granularity supported by the GPU when executing graphics operations. Because engines on the same adapter may potentially support different preemption levels, the driver should report the coarsest granularity among all engines capable of executing a particular type of graphics request.

For example, if one engine supports the preemption of primitive level graphics requests, and another engine supports the preemption of triangle level graphics requests, the driver should report a capability of <b>D3DKMDT_GRAPHICS_PREEMPTION_PRIMITIVE_BOUNDARY</b> for the  adapter.


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 8

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2012

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>D3dkmdt.h (include D3dkmdt.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="display.d3dkmdt_compute_preemption_granularity">D3DKMDT_COMPUTE_PREEMPTION_GRANULARITY</a>
</dt>
<dt>
<a href="display.d3dkmdt_preemption_caps">D3DKMDT_PREEMPTION_CAPS</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMDT_GRAPHICS_PREEMPTION_GRANULARITY enumeration%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
