---
UID: NF.wudfddi.IWDFIoRequest2.GetSetInformationParameters
title: IWDFIoRequest2::GetSetInformationParameters method
author: windows-driver-content
description: The GetSetInformationParameters method retrieves parameters that are associated with a WdfRequestSetInformation-typed I/O request.
old-location: wdf\iwdfiorequest2_getsetinformationparameters.htm
old-project: wdf
ms.assetid: 44872d92-4a71-4cc7-9f7c-c95477ac3264
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: IWDFIoRequest2, IWDFIoRequest2::GetSetInformationParameters, GetSetInformationParameters
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: wudfddi.h
req.include-header: Wudfddi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.9
req.alt-api: IWDFIoRequest2.GetSetInformationParameters
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: 
req.product: Windows 10 or later.
---

# IWDFIoRequest2::GetSetInformationParameters method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]

The <b>GetSetInformationParameters</b> method retrieves parameters that are associated with a <a href="wdf.wdf_request_type__umdf_">WdfRequestSetInformation</a>-typed I/O request.



## -syntax

````
void GetSetInformationParameters(
  [out, optional] WDF_FILE_INFORMATION_CLASS *pInformationClass,
  [out, optional] SIZE_T                     *pSizeInBytes
);
````


## -parameters

### -param pInformationClass [out, optional]

A pointer to a driver-allocated variable that receives a <a href="wdf.wdf_file_information_class">WDF_FILE_INFORMATION_CLASS</a>-typed value. This pointer is optional and can be <b>NULL</b>.


### -param pSizeInBytes [out, optional]

A pointer to a driver-allocated variable that receives the size, in bytes, of the file information. This pointer is optional and can be <b>NULL</b>.


## -returns
None.


## -remarks
Your driver can call <b>GetSetInformationParameters</b> to obtain the parameters that are associated with an I/O request, if the request type is <a href="wdf.wdf_request_type__umdf_">WdfRequestSetInformation</a>. The <i>pInformationClass</i> parameter identifies the type of file information that the driver should set, and the <i>pSizeInBytes</i> parameter specifies the size of the buffer that contains the information. The driver can call <a href="wdf.iwdfiorequest2_retrieveinputbuffer">IWDFIoRequest2::RetrieveInputBuffer</a> to obtain the buffer address. 

Your driver must verify that the specified buffer size is large enough to contain the file information that the driver must set.

The following code example is part of an <a href="wdf.iqueuecallbackdefaultiohandler_ondefaultiohandler">IQueueCallbackDefaultIoHandler::OnDefaultIoHandler</a> callback function. If the callback function receives a set information request, it retrieves the request's parameters. If the driver supports the specified type of information, it copies the information from the request's input buffer.


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
End of support

</th>
<td width="70%">
Unavailable in UMDF 2.0 and later.

</td>
</tr>
<tr>
<th width="30%">
Minimum UMDF version

</th>
<td width="70%">
1.9

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wudfddi.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\wudfddi\nn-wudfddi-iwdfiorequest2.md">IWDFIoRequest2</a>
</dt>
<dt>
<a href="wdf.iwdfiorequest2_getqueryinformationparameters">IWDFIoRequest2::GetQueryInformationParameters</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFIoRequest2::GetSetInformationParameters method%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
