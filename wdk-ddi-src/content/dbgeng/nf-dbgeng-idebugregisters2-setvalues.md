---
UID: NF.dbgeng.IDebugRegisters2.SetValues
title: IDebugRegisters2::SetValues method
author: windows-driver-content
description: The SetValues method sets the value of several of the target's registers.
old-location: debugger\setvalues.htm
old-project: Debugger
ms.assetid: 8f3817e7-8409-4b75-be28-ac7fe32145cb
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: IDebugRegisters2, IDebugRegisters2::SetValues, SetValues
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: dbgeng.h
req.include-header: DbgEng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugRegisters.SetValues,IDebugRegisters2.SetValues
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

# IDebugRegisters2::SetValues method



## -description
The <b>SetValues</b> method sets the value of several of the target's <a href="debugger.x86_architecture#registers#registers">registers</a>.



## -syntax

````
HRESULT SetValues(
  [in]           ULONG        Count,
  [in, optional] PULONG       Indices,
  [in]           ULONG        Start,
  [in]           PDEBUG_VALUE Values
);
````


## -parameters

### -param Count [in]

Specifies the number of registers for which to set the values.


### -param Indices [in, optional]

Specifies an array that contains the indices of the registers for which to set the values.  The number of elements in this array is <i>Count</i>.  If <i>Indices</i> is <b>NULL</b>, <i>Start</i> is used instead.


### -param Start [in]

If <i>Indices</i> is <b>NULL</b>, the registers will be set consecutively starting at this index.  Otherwise it is ignored.


### -param Values [in]

Specifies the array that contains values to which to set the registers.  The number of elements this array holds is <i>Count</i>.  See <a href="debugger.debug_value">DEBUG_VALUE</a> for a description of this parameter type.


## -returns
This list does not contain all the errors that might occur.  For a list of possible errors, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff549771">HRESULT Values</a>.
<dl>
<dt><b>S_OK</b></dt>
</dl>The method was successful.
<dl>
<dt><b>E_UNEXPECTED</b></dt>
</dl>The target is not accessible, or one or more of the registers could not be accessed.
<dl>
<dt><b>E_INVALIDARG</b></dt>
</dl>The value of the index of one or more of the registers is greater than the number of registers on the target machine.

 


## -remarks
The engine does its best to coerce the values in <i>Values</i> into the type of the registers; this coercion is the same as that performed by <a href="debugger.coercevalue">CoerceValue</a>.  If the value is larger than what the register can hold, the least significant bits are dropped.  Floating-point and integer conversions will also be performed if necessary.  

If the return value is not S_OK, some of the registers still might have been set.  

When a subregister is altered, the register containing it is also altered.

To set the value of only a single register, use the <a href="debugger.setvalue">SetValue</a> method instead.

The method <a href="debugger.setvalues2">SetValues2</a> performs the same task as this method but also allows the register source to be specified.

For an overview of the <a href="..\dbgeng\nn-dbgeng-idebugregisters.md">IDebugRegisters</a> interface and other register-related methods, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.


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
<dt>Dbgeng.h (include DbgEng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugregisters.md">IDebugRegisters</a>
</dt>
<dt>
<a href="..\dbgeng\nn-dbgeng-idebugregisters2.md">IDebugRegisters2</a>
</dt>
<dt>
<a href="debugger.setvalue">SetValue</a>
</dt>
<dt>
<a href="debugger.setvalues2">SetValues2</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Debugger\debugger]:%20IDebugRegisters::SetValues method%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
