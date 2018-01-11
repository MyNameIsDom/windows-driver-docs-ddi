---
UID: NC.d3d10umddi.PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE
title: PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE
author: windows-driver-content
description: The CalcPrivateDepthStencilStateSize function determines the size of the user-mode display driver's private region of memory (that is, the size of internal driver structures, not the size of the resource video memory) for a depth stencil state.
old-location: display\calcprivatedepthstencilstatesize.htm
old-project: display
ms.assetid: dcc02e1e-97e0-4ccd-8329-8219cad5d09a
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _SETRESULT_INFO, *PSETRESULT_INFO, PSETRESULT_INFO, SETRESULT_INFO
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CalcPrivateDepthStencilStateSize
req.alt-loc: d3d10umddi.h
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

# PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE callback



## -description
The <b>CalcPrivateDepthStencilStateSize</b> function determines the size of the user-mode display driver's private region of memory (that is, the size of internal driver structures, not the size of the resource video memory) for a depth stencil state.



## -prototype

````
PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE CalcPrivateDepthStencilStateSize;

SIZE_T APIENTRY CalcPrivateDepthStencilStateSize(
  _In_       D3D10DDI_HDEVICE             hDevice,
  _In_ const D3D10_DDI_DEPTH_STENCIL_DESC *pDepthStencilDesc
)
{ ... }
````


## -parameters

### -param hDevice [in]

 A handle to the display device (graphics context).


### -param pDepthStencilDesc [in]

 A pointer to a <a href="..\d3d10umddi\ns-d3d10umddi-d3d10_ddi_depth_stencil_desc.md">D3D10_DDI_DEPTH_STENCIL_DESC</a> structure that describes the parameters that the user-mode display driver uses to calculate the size of the memory region. 


## -returns
<b>CalcPrivateDepthStencilStateSize</b> returns the size of the memory region that the driver requires for creating a depth stencil state.


## -remarks
None.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows Vista and later versions of the Windows operating systems.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d10_ddi_depth_stencil_desc.md">D3D10_DDI_DEPTH_STENCIL_DESC</a>
</dt>
<dt>
<a href="..\d3d10umddi\ns-d3d10umddi-d3d10ddi_devicefuncs.md">D3D10DDI_DEVICEFUNCS</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE callback function%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
