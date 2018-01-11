---
UID: NI.ucmtcpciportcontrollerrequests.IOCTL_UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED
title: IOCTL_UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED
author: windows-driver-content
description: Notifies the client driver that an alternate mode is entered so that the driver can perform additional tasks.
old-location: buses\ioctl_ucmtcpci_port_controller_alternate_mode_entered.htm
old-project: UsbRef
ms.assetid: 6C9CECFD-E727-4586-BD86-6FC9272A37D0
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _UCMTCPCI_PORT_CONTROLLER_IOCTL, UCMTCPCI_PORT_CONTROLLER_IOCTL
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ucmtcpciportcontrollerrequests.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED
req.alt-loc: UcmTcpciPortControllerRequests.h
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

# IOCTL_UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED IOCTL



## -description
Notifies the client driver that an alternate mode is entered so that the driver can perform additional tasks.



## -ioctlparameters

### -input-buffer
A pointer to a <a href="buses.ucmtcpci_port_controller_alternate_mode_entered_in_params">UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED_IN_PARAMS</a> structure that contains information about the alternate mode. 


### -input-buffer-length
The size of <a href="buses.ucmtcpci_port_controller_alternate_mode_entered_in_params">UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED_IN_PARAMS</a>.


### -output-buffer

<text></text>

### -output-buffer-length

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. 


## -remarks
The UcmTcpciCx class extension sends this IOCTL request when an alternate mode is entered. The client driver can determine the alternate mode that was entered based on the values passed in <i>SVID</i> and <i>Mode</i> of the supplied structure.


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 10

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2016

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>UcmTcpciPortControllerRequests.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542894">Creating IOCTL Requests in Drivers</a>
</dt>
<dt>
<a href="wdf.wdfiotargetsendinternalioctlotherssynchronously">WdfIoTargetSendInternalIoctlOthersSynchronously</a>
</dt>
<dt>
<a href="wdf.wdfiotargetsendinternalioctlsynchronously">WdfIoTargetSendInternalIoctlSynchronously</a>
</dt>
<dt>
<a href="wdf.wdfiotargetsendioctlsynchronously">WdfIoTargetSendIoctlSynchronously</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [UsbRef\buses]:%20IOCTL_UCMTCPCI_PORT_CONTROLLER_ALTERNATE_MODE_ENTERED control code%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
