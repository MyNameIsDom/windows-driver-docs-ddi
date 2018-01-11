---
UID: NF.fwpsk.FwpsFlowAbort0
title: FwpsFlowAbort0 function
author: windows-driver-content
description: The FwpsFlowAbort0 function aborts a data flow.Note  FwpsFlowAbort0 is a specific version of FwpsFlowAbort.
old-location: netvista\fwpsflowabort0.htm
old-project: NetVista
ms.assetid: 029dd387-498f-4402-9e61-a46688294949
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: FwpsFlowAbort0
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FwpsFlowAbort0
req.alt-loc: fwpkclnt.lib,fwpkclnt.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fwpkclnt.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
---

# FwpsFlowAbort0 function



## -description
The <b>FwpsFlowAbort0</b> function aborts a data flow.<div class="alert"><b>Note</b>  <b>FwpsFlowAbort0</b> is a specific version of <b>FwpsFlowAbort</b>. See <a href="fwp.wfp_version-independent_names_and_targeting_specific_versions_of_windows">WFP Version-Independent Names and Targeting Specific Versions of Windows</a> for more information.</div>
<div> </div>




## -syntax

````
NTSTATUS NTAPI FwpsFlowAbort0(
  _In_ UINT64 flowId
);
````


## -parameters

### -param flowId [in]

A run-time identifier that specifies the data flow that is being aborted. The run-time identifier for a data flow is provided to a callout driver through the FWPS_METADATA_FIELD_FLOW_HANDLE metadata value that the filter engine provided to the callout driver's <a href="netvista.classifyfn">classifyFn</a> callout function.




## -returns
The 
     <b>FwpsFlowAbort0</b> function returns one of the following NTSTATUS codes.
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl>The flow was aborted. 
<dl>
<dt><b>Other status codes</b></dt>
</dl>An error occurred.

 


## -remarks

    A callout driver can call the <b>FwpsFlowAbort0</b> function to abort a data flow. 
   The filter engine calls the 
    <a href="..\fwpsk\nc-fwpsk-fwps_callout_flow_delete_notify_fn0.md">flowDeleteFn</a> callout function when the flow is terminated so that the callout driver can clean up
    the context associated with the flow.


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
Version

</th>
<td width="70%">
Available starting with Windows 8.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Fwpsk.h (include Fwpsk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Fwpkclnt.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;= DISPATCH_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\fwpsk\nc-fwpsk-fwps_callout_classify_fn0.md">classifyFn</a>
</dt>
<dt>
<a href="..\fwpsk\nc-fwpsk-fwps_callout_flow_delete_notify_fn0.md">flowDeleteFn</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [NetVista\netvista]:%20FwpsFlowAbort0 function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
