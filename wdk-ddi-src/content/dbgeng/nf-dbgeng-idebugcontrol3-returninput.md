---
UID: NF.dbgeng.IDebugControl3.ReturnInput
title: IDebugControl3::ReturnInput method
author: windows-driver-content
description: The ReturnInput method is used by IDebugInputCallbacks objects to send an input string to the engine following a request for input.
old-location: debugger\returninput.htm
old-project: Debugger
ms.assetid: 1f4c63da-8583-4382-a208-8279b4fe0906
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: IDebugControl3, IDebugControl3::ReturnInput, ReturnInput
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugControl.ReturnInput,IDebugControl2.ReturnInput,IDebugControl3.ReturnInput
req.alt-loc: dbgeng.h
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

# IDebugControl3::ReturnInput method



## -description
The <b>ReturnInput</b>  method is used by <b>IDebugInputCallbacks</b> objects to send an input string to the engine following a request for input.



## -syntax

````
HRESULT ReturnInput(
  [in] PCSTR Buffer
);
````


## -parameters

### -param Buffer [in]

Specifies the input string being sent to the engine.


## -returns
<dl>
<dt><b>S_OK</b></dt>
</dl>The method was successful.
<dl>
<dt><b>S_FALSE</b></dt>
</dl>The engine had already received the input it requested. The input string in <i>Buffer</i> was not received by the engine.

 

This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.


## -remarks
For an overview of input in the debugger engine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff550971">Input and Output</a>.


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
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>