---
UID: NF.fcb.RxCreateSrvCall
title: RxCreateSrvCall function
author: windows-driver-content
description: RxCreateSrvCall builds a SRV_CALL structure and inserts the name into the net name table maintained by RDBSS.
old-location: ifsk\rxcreatesrvcall.htm
old-project: ifsk
ms.assetid: 0eda9724-686f-4681-a1f0-92bdc36e695d
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: RxCreateSrvCall
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: fcb.h
req.include-header: Rxcontx.h, Mrxfcb.h, Prefix.h, Fcb.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxCreateSrvCall
req.alt-loc: fcb.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
---

# RxCreateSrvCall function



## -description
<b>RxCreateSrvCall</b> builds a SRV_CALL structure and inserts the name into the net name table maintained by RDBSS. 



## -syntax

````
PSRV_CALL RxCreateSrvCall(
  _In_     PRX_CONTEXT       RxContext,
  _In_     PUNICODE_STRING   Name,
  _In_opt_ PUNICODE_STRING   InnerNamePrefix,
  _In_     PRX_CONNECTION_ID RxConnectionId
);
````


## -parameters

### -param RxContext [in]

A pointer to the RX_CONTEXT structure containing the IRP describing a create operation.


### -param Name [in]

A pointer to the name to be inserted in the name table.


### -param InnerNamePrefix [in, optional]

A pointer to an optional inner prefix name to be inserted into the name table with the <i>Name</i>.


### -param RxConnectionId [in]

A pointer to the connection ID to be associated with the name to be inserted in the prefix name table. This parameter can be <b>NULL</b> in which case no connection ID will be associated with the name inserted in the prefix name table.


## -returns
<b>RxCreateSrvCall</b> returns a pointer to a newly created SRV_CALL data structure on success or a <b>NULL</b> pointer on failure. 


## -remarks
The <b>RxCreateSrvCall</b> routine is not normally called by network mini-redirector drivers directly. RDBSS calls this routine internally when an I/O request packet is received for IRP_MJ_CREATE and a SRV_CALL needs to be created. This IRP is normally received by RDBSS in response to a user-mode application requesting a file create operation on a network share. It is also possible for another kernel driver to issue such an IRP. 

Before calling <b>RxCreateSrvCall</b>, a lock on the name table associated with the device object member of the <i>RxContext</i> parameter must be acquired in exclusive mode. 

<b>RxCreateSrvCall</b> initializes the server call parameters passed in through extended attributes as part of the associated RX_CONTEXT structure. Currently this includes initializing the <b>pPrincipalName</b> member of the SRV_CALL which is passed in by the DFS driver. 


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
<dt>Fcb.h (include Rxcontx.h, Mrxfcb.h, Prefix.h, or Fcb.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;= APC_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.rxcreatenetfcb">RxCreateNetFcb</a>
</dt>
<dt>
<a href="ifsk.rxcreatenetfobx">RxCreateNetFobx</a>
</dt>
<dt>
<a href="ifsk.rxcreatenetroot">RxCreateNetRoot</a>
</dt>
<dt>
<a href="ifsk.rxcreatesrvopen">RxCreateSrvOpen</a>
</dt>
<dt>
<a href="ifsk.rxcreatevnetroot">RxCreateVNetRoot</a>
</dt>
<dt>
<a href="ifsk.rxdereference">RxDereference</a>
</dt>
<dt>
<a href="ifsk.rxfinalizeconnection">RxFinalizeConnection</a>
</dt>
<dt>
<a href="ifsk.rxfinalizenetfcb">RxFinalizeNetFcb</a>
</dt>
<dt>
<a href="ifsk.rxfinalizenetfobx">RxFinalizeNetFobx</a>
</dt>
<dt>
<a href="ifsk.rxfinalizenetroot">RxFinalizeNetRoot</a>
</dt>
<dt>
<a href="ifsk.rxfinalizesrvcall">RxFinalizeSrvCall</a>
</dt>
<dt>
<a href="ifsk.rxfinalizesrvopen">RxFinalizeSrvOpen</a>
</dt>
<dt>
<a href="ifsk.rxfinalizevnetroot">RxFinalizeVNetRoot</a>
</dt>
<dt>
<a href="ifsk.rxfinishfcbinitialization">RxFinishFcbInitialization</a>
</dt>
<dt>
<a href="ifsk.rxforcefinalizeallvnetroots">RxForceFinalizeAllVNetRoots</a>
</dt>
<dt>
<a href="ifsk.rxreference">RxReference</a>
</dt>
<dt>
<a href="ifsk.rxsetsrvcalldomainname">RxSetSrvCallDomainName</a>
</dt>
<dt>
<a href="ifsk.rxpdereferencenetfcb">RxpDereferenceNetFcb</a>
</dt>
<dt>
<a href="ifsk.rxpreferencenetfcb">RxpReferenceNetFcb</a>
</dt>
<dt>
<a href="ifsk.rx_context">RX_CONTEXT</a>
</dt>
<dt>
<a href="ifsk.the_srv_call_structure">The SRV_CALL Structure</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxCreateSrvCall function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
