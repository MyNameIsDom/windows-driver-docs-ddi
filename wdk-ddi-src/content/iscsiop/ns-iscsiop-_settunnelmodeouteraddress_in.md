---
UID: NS.ISCSIOP._SETTUNNELMODEOUTERADDRESS_IN
title: _SetTunnelModeOuterAddress_IN
author: windows-driver-content
description: The SetTunnelModeOuterAddress_IN structure holds the input data for the SetTunnelModeOuterAddress method.
old-location: storage\settunnelmodeouteraddress_in.htm
old-project: storage
ms.assetid: 3f698252-213f-482c-8c8f-624f0c370705
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _SetTunnelModeOuterAddress_IN, PSetTunnelModeOuterAddress_IN, SetTunnelModeOuterAddress_IN, *PSetTunnelModeOuterAddress_IN
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: iscsiop.h
req.include-header: Iscsiop.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SetTunnelModeOuterAddress_IN
req.alt-loc: iscsiop.h
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

# _SetTunnelModeOuterAddress_IN structure



## -description
The SetTunnelModeOuterAddress_IN structure holds the input data for the <a href="storage.settunnelmodeouteraddress">SetTunnelModeOuterAddress</a> method.



## -syntax

````
typedef struct _SetTunnelModeOuterAddress_IN {
  ULONG            PortNumber;
  ISCSI_IP_Address DestinationAddress;
  ISCSI_IP_Address TunnelModeOuterAddress;
} SetTunnelModeOuterAddress_IN, *PSetTunnelModeOuterAddress_IN;
````


## -struct-fields

### -field PortNumber

The number of the port to associate with the tunnel-mode address. A value of 0xffffffff associates the tunnel-mode address with all ports.


### -field DestinationAddress

An <a href="storage.iscsi_ip_address">ISCSI_IP_Address</a> structure that indicates the destination IP address in a way that is independent of the version of IP protocol in use.  


### -field TunnelModeOuterAddress

An ISCSI_IP_Address structure that indicates the IP address of the security gateway (tunnel-mode outer address) in a way that is independent of the version of IP protocol in use.


## -remarks
You must implement this method.


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Iscsiop.h (include Iscsiop.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.iscsi_ip_address">ISCSI_IP_Address</a>
</dt>
<dt>
<a href="storage.settunnelmodeouteraddress">SetTunnelModeOuterAddress</a>
</dt>
<dt>
<a href="storage.settunnelmodeouteraddress_out">SetTunnelModeOuterAddress_OUT</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20SetTunnelModeOuterAddress_IN structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
