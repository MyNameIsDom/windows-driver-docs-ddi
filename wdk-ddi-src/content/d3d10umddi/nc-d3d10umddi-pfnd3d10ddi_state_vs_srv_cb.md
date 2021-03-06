---
UID: NC:d3d10umddi.PFND3D10DDI_STATE_VS_SRV_CB
title: PFND3D10DDI_STATE_VS_SRV_CB
author: windows-driver-content
description: The pfnStateVsSrvCb function causes the Microsoft Direct3D 10 runtime to refresh the vertex shader stage's bound shader resource views.
old-location: display\pfnstatevssrvcb.htm
old-project: display
ms.assetid: 5102104e-b79c-40e5-87de-9ccf848288db
ms.author: windowsdriverdev
ms.date: 4/16/2018
ms.keywords: PFND3D10DDI_STATE_VS_SRV_CB, PFND3D10DDI_STATE_VS_SRV_CB callback, d3d10state_functions_18fed75e-bd90-41af-9ddd-d68c80f6afd7.xml, d3d10umddi/pfnStateVsSrvCb, display.pfnstatevssrvcb, pfnStateVsSrvCb, pfnStateVsSrvCb callback function [Display Devices]
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	d3d10umddi.h
api_name:
-	pfnStateVsSrvCb
product:
- Windows
targetos: Windows
req.typenames: 
---

# PFND3D10DDI_STATE_VS_SRV_CB callback function


## -description


The <b>pfnStateVsSrvCb</b> function causes the Microsoft Direct3D 10 runtime to refresh the vertex shader stage's bound shader resource views.


## -parameters




### -param Arg1


### -param Arg2


### -param Arg3








#### - Base [in]

 The beginning of the DDI handles to resource views. 


#### - Count [in]

 The total number of DDI handles to resource views. The number can be -1, which specifies that <b>pfnStateVsSrvCb</b> will use its high watermarks to substitute an optimal value (which is typically less than the maximum valid value for <i>Count</i>). However, no non-NULL binding exists in a slot larger than the optimal <i>Count</i> value.


#### - hRuntimeDevice [in]

 A handle to a context for the core Direct3D 10 runtime. This handle is supplied to the driver in a call to the driver's <a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a> function. 


## -returns



None




## -see-also




<a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff541820">D3D10DDI_CORELAYER_DEVICECALLBACKS</a>
 

 

