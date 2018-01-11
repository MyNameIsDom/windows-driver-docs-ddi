---
UID: NS.IRB._IDE_MINIPORT_RESOURCES
title: _IDE_MINIPORT_RESOURCES
author: windows-driver-content
description: The IDE_MINIPORT_RESOURCES structure is used by the port driver to provide the miniport driver with resources.Note  The ATA port driver and ATA miniport driver models may be altered or unavailable in the future.
old-location: storage\ide_miniport_resources.htm
old-project: storage
ms.assetid: 867b6152-9846-484f-9eac-07d0f24d55df
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _IDE_MINIPORT_RESOURCES, PIDE_MINIPORT_RESOURCES, *PIDE_MINIPORT_RESOURCES, IDE_MINIPORT_RESOURCES
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: irb.h
req.include-header: Irb.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDE_MINIPORT_RESOURCES
req.alt-loc: irb.h
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

# _IDE_MINIPORT_RESOURCES structure



## -description
The IDE_MINIPORT_RESOURCES structure is used by the port driver to provide the miniport driver with resources.



## -syntax

````
typedef struct _IDE_MINIPORT_RESOURCES {
  ULONG             NumberOfAccessRanges;
  PIDE_ACCESS_RANGE IdeAccessRange;
} IDE_MINIPORT_RESOURCES, *PIDE_MINIPORT_RESOURCES;
````


## -struct-fields

### -field NumberOfAccessRanges

Contains the number of access ranges pointed to by <b>IdeAccessRange</b>. Each is a range either of memory addresses or I/O port addresses.


### -field IdeAccessRange

Pointer to the first address range in a series of contiguous address ranges defined by a structure of type <a href="storage.ide_access_range">IDE_ACCESS_RANGE</a>. The value in the <b>NumberOfAccessRanges</b> member indicates how many address ranges are provided. The port driver populates each <b>IDE_ACCESS_RANGE</b> structure with the address ranges allocated for the controller.


## -remarks
The port driver passes this structure to the miniport driver's <a href="storage.idehwcontrol">IdeHwControl</a> routine.


## -requirements
<table>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Irb.h (include Irb.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="storage.ide_access_range">IDE_ACCESS_RANGE</a>
</dt>
<dt>
<a href="storage.idehwcontrol">IdeHwControl</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20IDE_MINIPORT_RESOURCES structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
