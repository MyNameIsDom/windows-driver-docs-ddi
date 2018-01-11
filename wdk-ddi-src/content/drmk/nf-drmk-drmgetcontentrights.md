---
UID: NF.drmk.DrmGetContentRights
title: DrmGetContentRights function
author: windows-driver-content
description: The DrmGetContentRights function retrieves the DRM content rights assigned to a DRM content ID.
old-location: audio\drmgetcontentrights.htm
old-project: audio
ms.assetid: 706a5749-e288-4275-84fc-e500a848d541
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: DrmGetContentRights
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: drmk.h
req.include-header: Drmk.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DrmGetContentRights
req.alt-loc: Drmk.lib,Drmk.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Drmk.lib
req.dll: 
req.irql: PASSIVE_LEVEL
---

# DrmGetContentRights function



## -description
The <code>DrmGetContentRights</code> function retrieves the DRM content rights assigned to a DRM content ID.



## -syntax

````
NTSTATUS DrmGetContentRights(
  _In_  ULONG      ContentId,
  _Out_ PDRMRIGHTS DrmRights
);
````


## -parameters

### -param ContentId [in]

Specifies the DRM content ID. This parameter identifies a KS audio stream.


### -param DrmRights [out]

Specifies the DRM content rights that are assigned to the stream that is identified by <i>ContentId</i>. This parameter is a pointer to a <a href="audio.drmrights">DRMRIGHTS</a> structure.


## -returns
<code>DrmGetContentRights</code> returns STATUS_SUCCESS if the call was successful. Otherwise, it returns an appropriate error code.


## -remarks
Before a KS audio filter begins mixing together several KS audio streams, it first calls <a href="audio.drmcreatecontentmixed">DrmCreateContentMixed</a> to create a content ID for the composite stream. Next, it calls <code>DrmGetContentRights</code> to get the content rights that the system has assigned to the stream.

A module that lies downstream from the KS filter that creates the content ID typically does not need to call <code>DrmGetContentRights</code>. Instead, the module receives both the content ID and content rights either from the system (through an <a href="audio.idrmaudiostream_setcontentid">IDrmAudioStream::SetContentId</a> call or a <a href="https://msdn.microsoft.com/library/windows/hardware/ff537351">KSPROPERTY_DRMAUDIOSTREAM_CONTENTID</a>set-property request) or directly from the preceding module in the data path (through a call to a content handler). For more information, see <a href="audio.drmforwardcontenttointerface">DrmForwardContentToInterface</a>, <a href="audio.drmforwardcontenttodeviceobject">DrmForwardContentToDeviceObject</a>, and <a href="audio.drmaddcontenthandlers">DrmAddContentHandlers</a>.

<code>DrmGetContentRights</code> performs the same function as <a href="audio.pcgetcontentrights">PcGetContentRights</a> and <a href="audio.idrmport_getcontentrights">IDrmPort::GetContentRights</a>. For more information, see <a href="https://msdn.microsoft.com/62c739da-91e8-428e-b76c-ec9621b12597">DRM Functions and Interfaces</a>.


## -requirements
<table>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Drmk.h (include Drmk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Drmk.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
PASSIVE_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="audio.drmrights">DRMRIGHTS</a>
</dt>
<dt>
<a href="audio.drmcreatecontentmixed">DrmCreateContentMixed</a>
</dt>
<dt>
<a href="audio.idrmaudiostream_setcontentid">IDrmAudioStream::SetContentId</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537351">KSPROPERTY_DRMAUDIOSTREAM_CONTENTID</a>
</dt>
<dt>
<a href="audio.drmforwardcontenttointerface">DrmForwardContentToInterface</a>
</dt>
<dt>
<a href="audio.drmforwardcontenttodeviceobject">DrmForwardContentToDeviceObject</a>
</dt>
<dt>
<a href="audio.drmaddcontenthandlers">DrmAddContentHandlers</a>
</dt>
<dt>
<a href="audio.pcgetcontentrights">PcGetContentRights</a>
</dt>
<dt>
<a href="audio.idrmport_getcontentrights">IDrmPort::GetContentRights</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20DrmGetContentRights function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
