---
UID: NF.ntddk.RtlLeftChild
title: RtlLeftChild macro
author: windows-driver-content
description: The RtlLeftChild routine returns a pointer to the left child of the specified splay link node.
old-location: ifsk\rtlleftchild.htm
old-project: ifsk
ms.assetid: 26e6b0c6-7de0-43c9-a117-5c0bf0e986a2
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: RtlLeftChild
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: macro
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlLeftChild
req.alt-loc: ntddk.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section.
---

# RtlLeftChild macro



## -description
The <b>RtlLeftChild</b> routine returns a pointer to the left child of the specified splay link node. 



## -syntax

````
PRTL_SPLAY_LINKS RtlLeftChild(
  _In_ PRTL_SPLAY_LINKS Links
);
````


## -parameters

### -param Links [in]

Pointer to the node whose left child is to be returned. The node must have been initialized by calling <b>RtlInitializeSplayLinks</b>. 


## -remarks
<b>RtlLeftChild</b> can be called repeatedly in conjunction with <b>RtlParent</b> and <b>RtlRightChild</b> to walk a splay link tree. 

Callers of the <b>Rtl</b> splay link routines are responsible for synchronizing access to the splay link tree. A fast mutex is the most efficient synchronization mechanism to use for this purpose. 

Callers of <b>RtlLeftChild</b> must be running at IRQL &lt;= DISPATCH_LEVEL if the tree is nonpaged. Usually, callers are running at IRQL PASSIVE_LEVEL. 


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
Header

</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
See Remarks section.

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.rtlinitializesplaylinks">RtlInitializeSplayLinks</a>
</dt>
<dt>
<a href="ifsk.rtlinsertasleftchild">RtlInsertAsLeftChild</a>
</dt>
<dt>
<a href="ifsk.rtlparent">RtlParent</a>
</dt>
<dt>
<a href="ifsk.rtlrightchild">RtlRightChild</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlLeftChild routine%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
