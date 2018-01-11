---
UID: NS.MFAPI.TAGCAPTUREDMETADATAWHITEBALANCEGAINS
title: tagCapturedMetadataWhiteBalanceGains
author: windows-driver-content
description: This structure describes the blob format for the MF_CAPTURE_METADATA_WHITEBALANCE_GAINS attribute.
old-location: stream\capturedmetadatawhitebalancegains.htm
old-project: stream
ms.assetid: 1F844204-0709-4203-80C5-C90949F96159
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: tagCapturedMetadataWhiteBalanceGains, CapturedMetadataWhiteBalanceGains
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: mfapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CapturedMetadataWhiteBalanceGains
req.alt-loc: mfapi.h
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

# tagCapturedMetadataWhiteBalanceGains structure



## -description
This structure describes the blob format for the <b>MF_CAPTURE_METADATA_WHITEBALANCE_GAINS</b> attribute.  



## -syntax

````
typedef struct tagCapturedMetadataWhiteBalanceGains {
  FLOAT R;
  FLOAT G;
  FLOAT B;
} CapturedMetadataWhiteBalanceGains;
````


## -struct-fields

### -field R

The  <b>R</b> value of the blob.


### -field G

The  <b>G</b> value of the blob.


### -field B

The  <b>B</b> value of the blob.


## -remarks
The <b>MF_CAPTURE_METADATA_WHITEBALANCE_GAINS</b> attribute contains the white balance gains applied to R, G, B by the sensor or ISP when the preview frame was captured. This is a unitless.

The <b>CapturedMetadataWhiteBalanceGains</b> structure only describes the blob format for the <b>MF_CAPTURE_METADATA_WHITEBALANCE_GAINS</b> attribute.  The metadata item structure for white balance gains (<a href="stream.kscamera_metadata_itemheader">KSCAMERA_METADATA_ITEMHEADER</a> + white balance gains metadata payload) is up to driver and must be 8-byte aligned.


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Mfapi.h</dt>
</dl>
</td>
</tr>
</table>