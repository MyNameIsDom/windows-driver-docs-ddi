---
UID: NI.ntddcdrm.IOCTL_CDROM_GET_CONFIGURATION
title: IOCTL_CDROM_GET_CONFIGURATION
author: windows-driver-content
description: Requests feature and profile information from a CD-ROM device.
old-location: storage\ioctl_cdrom_get_configuration.htm
old-project: storage
ms.assetid: 2eb4b5c3-db06-4d21-8937-847734d7ac2f
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _WRITE_ROTATION, *PWRITE_ROTATION, PWRITE_ROTATION, WRITE_ROTATION
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ntddcdrm.h
req.include-header: Ntddcdrm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_CDROM_GET_CONFIGURATION
req.alt-loc: ntddcdrm.h
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

# IOCTL_CDROM_GET_CONFIGURATION IOCTL



## -description

Requests feature and profile information from a CD-ROM device. 

Multimedia devices have different characteristics depending on the type of media that is in the device. To provide drivers with a means of querying multimedia devices about these varying characteristics, the <i>SCSI Multimedia - 3</i> (<i>MMC-3</i>) specification defines a command called "GET CONFIGURATION." This command permits drivers to query a device for both permanent information about the device and information that varies whenever the media changes. In Microsoft Windows 2000 and later operating systems, drivers can send this query to a device using the IOCTL_CDROM_GET_CONFIGURATION request. 

The IOCTL_CDROM_GET_CONFIGURATION request returns a list of descriptors that describe the capabilities of the device for the current medium. These descriptors are divided into two groups called "feature descriptors" and "profile list descriptors." A feature specifies the capabilities of a device and its associated medium. A profile is a collection of features. If the device supports a profile, it supports all the features in the profile. 

See the <i>MMC-3</i> specification for further discussion concerning features and profiles.



Requests feature and profile information from a CD-ROM device. 

Multimedia devices have different characteristics depending on the type of media that is in the device. To provide drivers with a means of querying multimedia devices about these varying characteristics, the <i>SCSI Multimedia - 3</i> (<i>MMC-3</i>) specification defines a command called "GET CONFIGURATION." This command permits drivers to query a device for both permanent information about the device and information that varies whenever the media changes. In Microsoft Windows 2000 and later operating systems, drivers can send this query to a device using the IOCTL_CDROM_GET_CONFIGURATION request. 

The IOCTL_CDROM_GET_CONFIGURATION request returns a list of descriptors that describe the capabilities of the device for the current medium. These descriptors are divided into two groups called "feature descriptors" and "profile list descriptors." A feature specifies the capabilities of a device and its associated medium. A profile is a collection of features. If the device supports a profile, it supports all the features in the profile. 

See the <i>MMC-3</i> specification for further discussion concerning features and profiles.



## -ioctlparameters

### -input-buffer
Input buffer.


### -input-buffer-length
<b>Parameters.DeviceIoControl.InputBufferLength</b> in the IO_STACK_LOCATION structure indicates the size, in bytes, of the input buffer, which must be = <b>sizeof</b>(GET_CONFIGURATION_IOCTL_INPUT).


### -output-buffer
The driver returns the feature and profile data in the buffer at <b>Irp-&gt;AssociatedIrp.SystemBuffer</b>. The data begins with a header of type <a href="storage.get_configuration_header">GET_CONFIGURATION_HEADER</a>. Feature data is reported in the space immediately following this header. Its size and formatting depend on which features are reported. 


### -output-buffer-length
<b>Parameters.DeviceIoControl.OutputBufferLength</b> in the I/O stack location indicates the size, in bytes, of the buffer, which must be &gt;= <b>sizeof</b>(GET_CONFIGURATION_HEADER).


### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
The <b>Information</b> field is set to the number of bytes that are returned. The <b>Status</b> field is set to STATUS_SUCCESS if the request succeeds. If the <b>Parameters.DeviceIoControl.InputBufferLength</b> does not have the correct value, the request fails with a STATUS_INFO_LENGTH_MISMATCH error. If <b>Parameters.DeviceIoControl.OutputBufferLength</b> is not large enough, the request fails with a STATUS_BUFFER_TOO_SMALL error. If the value for the output buffer is too large, the request fails a STATUS_INVALID_BUFFER_SIZE message. 


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntddcdrm.h (include Ntddcdrm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.get_configuration_ioctl_input">GET_CONFIGURATION_IOCTL_INPUT</a>
</dt>
<dt>
<a href="storage.get_configuration_header">GET_CONFIGURATION_HEADER</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20IOCTL_CDROM_GET_CONFIGURATION control code%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
