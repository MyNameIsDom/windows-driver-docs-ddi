---
UID: NS.ISCSIFND._ISCSI_DISCOVEREDTARGETPORTALGROUP
title: _ISCSI_DiscoveredTargetPortalGroup
author: windows-driver-content
description: The ISCSI_DiscoveredTargetPortalGroup structure contains information about a discovered target portal group.
old-location: storage\iscsi_discoveredtargetportalgroup.htm
old-project: storage
ms.assetid: 5c90dbc2-f42a-4c04-8c77-0ef3a712416c
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _ISCSI_DiscoveredTargetPortalGroup, PISCSI_DiscoveredTargetPortalGroup, ISCSI_DiscoveredTargetPortalGroup, *PISCSI_DiscoveredTargetPortalGroup
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: iscsifnd.h
req.include-header: Iscsifnd.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ISCSI_DiscoveredTargetPortalGroup
req.alt-loc: iscsifnd.h
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

# _ISCSI_DiscoveredTargetPortalGroup structure



## -description
The ISCSI_DiscoveredTargetPortalGroup structure contains information about a discovered target portal group.



## -syntax

````
typedef struct _ISCSI_DiscoveredTargetPortalGroup {
  ULONG                        PortalCount;
  ISCSI_DiscoveredTargetPortal Portals[1];
} ISCSI_DiscoveredTargetPortalGroup, *PISCSI_DiscoveredTargetPortalGroup;
````


## -struct-fields

### -field PortalCount

The number of portals in the group. 


### -field Portals

An array of <a href="storage.iscsi_discoveredtargetportal">ISCSI_DiscoveredTargetPortal</a> structures, which describe target portals. 


## -remarks
The WMI tool suite automatically generates a declaration of the ISCSI_DiscoveredTargetPortalGroup structure when it compiles the <a href="storage.iscsi_discoveredtargetportalgroup_wmi_class">ISCSI_DiscoveredTargetPortalGroup WMI Class</a> in <i>Discover.mof</i>. 


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Iscsifnd.h (include Iscsifnd.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.iscsi_discoveredtargetportal">ISCSI_DiscoveredTargetPortal</a>
</dt>
<dt>
<a href="storage.iscsi_discoveredtargetportalgroup2">ISCSI_DiscoveredTargetPortalGroup2</a>
</dt>
<dt>
<a href="storage.iscsi_discoveredtargetportalgroup_wmi_class">ISCSI_DiscoveredTargetPortalGroup WMI Class</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20ISCSI_DiscoveredTargetPortalGroup structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
