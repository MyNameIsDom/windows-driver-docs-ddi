---
UID: NS.WDM._EXT_SET_PARAMETERS_V0
title: _EXT_SET_PARAMETERS_V0
author: windows-driver-content
description: The EXT_SET_PARAMETERS structure contains an extended set of parameters for the ExSetTimer routine.
old-location: kernel\ext_set_parameters.htm
old-project: kernel
ms.assetid: 8872AA79-1D54-4952-A45E-A2DB97730CA7
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: _EXT_SET_PARAMETERS_V0, *PEXT_SET_PARAMETERS, PEXT_SET_PARAMETERS, EXT_SET_PARAMETERS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with Windows 8.1.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: EXT_SET_PARAMETERS
req.alt-loc: Wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
req.product: Windows 10 or later.
---

# _EXT_SET_PARAMETERS_V0 structure



## -description
The <b>EXT_SET_PARAMETERS</b> structure contains an extended set of parameters for the <a href="kernel.exsettimer">ExSetTimer</a> routine.



## -syntax

````
typedef struct _EXT_SET_PARAMETERS {
  ULONG    Version;
  ULONG    Reserved;
  LONGLONG NoWakeTolerance;
} EXT_SET_PARAMETERS, *PEXT_SET_PARAMETERS;
````


## -struct-fields

### -field Version

The version number of this <b>EXT_SET_PARAMETERS</b> structure. The <a href="kernel.exinitializesettimerparameters">ExInitializeSetTimerParameters</a> routine sets this member to the correct version number.


### -field Reserved

Set to zero. The <b>ExInitializeSetTimerParameters</b> routine sets this member to zero.


### -field NoWakeTolerance

The maximum time, in system time units (100-nanosecond intervals), that the timer can wait to wake the processor after the timer reaches its expiration time. Only after the processor wakes can the timer expire. If a timer is set to expire when the processor is in a low-power state, the timer will not wake the processor to expire until the expiration time plus the <b>NoWakeTolerance</b> delay is exceeded. As an option, a driver can set this member to EX_TIMER_UNLIMITED_TOLERANCE, which indicates that the timer never wakes the processor and, thus, cannot expire until the processor wakes for some other reason.

Do not set this member to a negative value (other than EX_TIMER_UNLIMITED_TOLERANCE). Otherwise, the routine bug checks.


## -remarks
The <i>Parameters</i> parameter of the <a href="kernel.exsettimer">ExSetTimer</a> routine is a pointer to an <b>EXT_SET_PARAMETERS</b> structure. Before passing an <b>EXT_SET_PARAMETERS</b> structure to this routine, call the <a href="kernel.exinitializesettimerparameters">ExInitializeSetTimerParameters</a> routine to initialize the structure.


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported starting with Windows 8.1.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.exinitializesettimerparameters">ExInitializeSetTimerParameters</a>
</dt>
<dt>
<a href="kernel.exsettimer">ExSetTimer</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20EXT_SET_PARAMETERS structure%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
