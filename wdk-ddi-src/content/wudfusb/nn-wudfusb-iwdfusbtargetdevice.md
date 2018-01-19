---
UID : NN:wudfusb.IWDFUsbTargetDevice
title : IWDFUsbTargetDevice
author : windows-driver-content
description : The IWDFUsbTargetDevice interface exposes a USB device I/O target object.
old-location : wdf\iwdfusbtargetdevice.htm
old-project : wdf
ms.assetid : 627a4633-6857-43a5-af2d-36e4e554ca83
ms.author : windowsdriverdev
ms.date : 1/11/2018
ms.keywords : IWDFUsbTargetPipe2, IWDFUsbTargetPipe2::ConfigureContinuousReader, ConfigureContinuousReader
ms.prod : windows-hardware
ms.technology : windows-devices
ms.topic : interface
req.header : wudfusb.h
req.include-header : 
req.target-type : Desktop
req.target-min-winverclnt : 
req.target-min-winversvr : 
req.kmdf-ver : 
req.umdf-ver : 1.5
req.alt-api : IWDFUsbTargetDevice
req.alt-loc : WUDFx.dll
req.ddi-compliance : 
req.unicode-ansi : 
req.idl : 
req.max-support : Unavailable in UMDF 2.0 and later.
req.namespace : 
req.assembly : 
req.type-library : 
req.lib : 
req.dll : WUDFx.dll
req.irql : 
req.typenames : "*PWDF_USB_REQUEST_TYPE, WDF_USB_REQUEST_TYPE"
req.product : Windows 10 or later.
---

# IWDFUsbTargetDevice interface

<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]


The <b>IWDFUsbTargetDevice</b> interface exposes a USB device I/O target object.



The <b>IWDFUsbTargetDevice</b> interface exposes a USB device I/O target object.

## Methods

<p>The <b>IWDFUsbTargetDevice</b> interface has these methods.</p>

| Method | Description |
| ---- |:---- |
| [wudfusb.IWDFUsbTargetDevice.FormatRequestForControlTransfer](nf-wudfusb-iwdfusbtargetdevice-formatrequestforcontroltransfer.md) | The FormatRequestForControlTransfer method formats an I/O request object for a USB control transfer. |
| [wudfusb.IWDFUsbTargetDevice.GetNumInterfaces](nf-wudfusb-iwdfusbtargetdevice-getnuminterfaces.md) | The GetNumInterfaces method retrieves the number of USB interfaces for the USB device. |
| [wudfusb.IWDFUsbTargetDevice.GetWinUsbHandle](nf-wudfusb-iwdfusbtargetdevice-getwinusbhandle.md) | The GetWinUsbHandle method retrieves the WinUsb interface handle that is associated with a I/O target device object. |
| [wudfusb.IWDFUsbTargetDevice.RetrieveDescriptor](nf-wudfusb-iwdfusbtargetdevice-retrievedescriptor.md) | The RetrieveDescriptor method retrieves a USB descriptor, which can describe a device, configuration, or string. |
| [wudfusb.IWDFUsbTargetDevice.RetrieveDeviceInformation](nf-wudfusb-iwdfusbtargetdevice-retrievedeviceinformation.md) | The RetrieveDeviceInformation method retrieves device information of the specified type. |
| [wudfusb.IWDFUsbTargetDevice.RetrievePowerPolicy](nf-wudfusb-iwdfusbtargetdevice-retrievepowerpolicy.md) | The RetrievePowerPolicy method retrieves a WinUsb power policy. |
| [wudfusb.IWDFUsbTargetDevice.RetrieveUsbInterface](nf-wudfusb-iwdfusbtargetdevice-retrieveusbinterface.md) | The RetrieveUsbInterface method retrieves the specified USB interface for a USB device. |
| [wudfusb.IWDFUsbTargetDevice.SetPowerPolicy](nf-wudfusb-iwdfusbtargetdevice-setpowerpolicy.md) | The SetPowerPolicy method sets the WinUsb power policy. |

## Remarks



## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows Driver kit version** |  |
| **Target platform** | Desktop |
| **Minimum UMDF version** | 1.5 |
| **Header** | wudfusb.h |
| **DLL** | WUDFx.dll |