---
UID : NN:wia_lh.IWiaErrorHandler
title : IWiaErrorHandler
author : windows-driver-content
description : The IWiaErrorHandler interface provides the GetStatusDescription and ReportStatus methods, which enable minidrivers to give users information about status or errors during a data transfer and possibly give an opportunity to recover from errors.
old-location : image\iwiaerrorhandler_interface.htm
old-project : image
ms.assetid : b441fbca-75fe-4b9d-a9d5-2ad5a4a55801
ms.author : windowsdriverdev
ms.date : 1/17/2018
ms.keywords : IWiaTransferCallback, IWiaTransferCallback::TransferCallback, TransferCallback
ms.prod : windows-hardware
ms.technology : windows-devices
ms.topic : interface
req.header : wia_lh.h
req.include-header : 
req.target-type : Windows
req.target-min-winverclnt : 
req.target-min-winversvr : 
req.kmdf-ver : 
req.umdf-ver : 
req.alt-api : IWiaErrorHandler
req.alt-loc : wia_lh.h
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
req.typenames : BMP_IMAGE_INFO, *PBMP_IMAGE_INFO
req.product : Windows 10 or later.
---

# IWiaErrorHandler interface

The <b>IWiaErrorHandler</b> interface provides the <a href="https://msdn.microsoft.com/c3b5622d-9d51-4008-abb0-c8a60c4a6b16">GetStatusDescription</a> and <a href="https://msdn.microsoft.com/c244d5a1-d3c1-4f8f-9b55-3729e5f13887">ReportStatus</a> methods, which enable minidrivers to give users information about status or errors during a data transfer and possibly give an opportunity to recover from errors.

## Methods

<p>The <b>IWiaErrorHandler</b> interface has these methods.</p>

| Method | Description |
| ---- |:---- |
| [wia_lh.IWiaErrorHandler.GetStatusDescription](nf-wia_lh-iwiaerrorhandler-getstatusdescription.md) | The system UI calls the GetStatusDescription method to provide the user with extra information about an error, if the user requests this information. This method is implemented by a driver's UI extension. |
| [wia_lh.IWiaErrorHandler.ReportStatus](nf-wia_lh-iwiaerrorhandler-reportstatus.md) | The ReportStatus method displays information about an error or status during a transfer. In some cases this method allows the user to recover from an error. |

## Remarks



## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows Driver kit version** |  |
| **Target platform** | Windows |
| **Minimum UMDF version** |  |
| **Header** | wia_lh.h |
| **DLL** |  |