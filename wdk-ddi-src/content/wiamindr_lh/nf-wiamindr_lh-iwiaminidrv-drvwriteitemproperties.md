---
UID: NF.wiamindr_lh.IWiaMiniDrv.drvWriteItemProperties
title: IWiaMiniDrv::drvWriteItemProperties method
author: windows-driver-content
description: The IWiaMiniDrv::drvWriteItemProperties method writes driver item properties to a WIA hardware device.
old-location: image\iwiaminidrv_drvwriteitemproperties.htm
old-project: Image
ms.assetid: 350cb7f6-499f-4fbc-b5c0-6f4daf2a2af0
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: IWiaMiniDrv, IWiaMiniDrv::drvWriteItemProperties, drvWriteItemProperties
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: wiamindr_lh.h
req.include-header: Wiamindr.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Me and in Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IWiaMiniDrv.drvWriteItemProperties
req.alt-loc: wiamindr_lh.h
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

# IWiaMiniDrv::drvWriteItemProperties method



## -description
The <b>IWiaMiniDrv::drvWriteItemProperties</b> method writes driver item properties to a WIA hardware device.



## -syntax

````
HRESULT drvWriteItemProperties(
  [in]  BYTE                      *pWiasContext,
  [in]  LONG                      lFlags,
  [in]  PMINIDRV_TRANSFER_CONTEXT pmdtc,
  [out] LONG                      *plDevErrVal
);
````


## -parameters

### -param pWiasContext [in]

Pointer to a WIA item context.


### -param lFlags [in]

Is currently unused. 


### -param pmdtc [in]

Points to a <a href="image.minidrv_transfer_context">MINIDRV_TRANSFER_CONTEXT</a> structure containing the device transfer context.


### -param plDevErrVal [out]

Points to a memory location that will receive a status code for this method. If this method returns S_OK, the value stored will be zero. Otherwise, a minidriver-specific error code will be stored at the location pointed to by this parameter.


## -returns
On success, the method should return S_OK and clear the device error value pointed to by <i>plDevErrVal</i>. If the method fails, it should return a standard COM error code and place a minidriver-specific error code value in the memory pointed to by <i>plDevErrVal</i>.

The value pointed to by <i>plDevErrVal</i> can be converted to a string by calling <a href="image.iwiaminidrv_drvgetdeviceerrorstr">IWiaMiniDrv::drvGetDeviceErrorStr</a>.


## -remarks


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
Available in Windows Me and in Windows XP and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wiamindr_lh.h (include Wiamindr.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="image.wiasgetrootitem">wiasGetRootItem</a>
</dt>
<dt>
<a href="image.wiasreadpropstr">wiasReadPropStr</a>
</dt>
<dt>
<a href="image.wiasreadproplong">wiasReadPropLong</a>
</dt>
<dt>
<a href="image.wiasreadpropbin">wiasReadPropBin</a>
</dt>
<dt>
<a href="image.wiasreadpropfloat">wiasReadPropFloat</a>
</dt>
<dt>
<a href="image.wiasreadpropguid">wiasReadPropGuid</a>
</dt>
<dt>
<a href="image.wiasreadmultiple">wiasReadMultiple</a>
</dt>
<dt>
<a href="image.iwiaminidrv_drvgetdeviceerrorstr">IWiaMiniDrv::drvGetDeviceErrorStr</a>
</dt>
<dt>
<a href="image.iwiaminidrv_drvreaditemproperties">IWiaMiniDrv::drvReadItemProperties</a>
</dt>
<dt>
<a href="image.minidrv_transfer_context">MINIDRV_TRANSFER_CONTEXT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Image\image]:%20IWiaMiniDrv::drvWriteItemProperties method%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
