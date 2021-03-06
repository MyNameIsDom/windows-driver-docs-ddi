---
UID: NF:ntintsafe.RtlLongLongToInt
title: RtlLongLongToInt function
author: windows-driver-content
description: Converts a value of type LONGLONG to a value of type INT.
old-location: kernel\rtllonglongtoint.htm
old-project: kernel
ms.assetid: CED66199-041A-432D-99C6-002D7BC83775
ms.author: windowsdriverdev
ms.date: 4/30/2018
ms.keywords: RtlLongLongToInt, RtlLongLongToInt function [Kernel-Mode Driver Architecture], kernel.rtllonglongtoint, ntintsafe/RtlLongLongToInt
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntintsafe.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
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
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	Ntintsafe.h
api_name:
-	RtlLongLongToInt
product:
- Windows
targetos: Windows
req.typenames: 
---

# RtlLongLongToInt function


## -description


Converts a value of type <b>LONGLONG</b> to a value of type <b>INT</b>.


## -parameters




### -param llOperand [in]

The value to be converted.


### -param piResult [out]

A pointer to the converted value. In the case where the conversion causes a truncation of the original value, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.


## -remarks



This is one of a set of inline functions designed to provide type conversions and perform validity checks with minimal impact on performance.

This function uses the following alternate name:

<ul>
<li>RtlIntPtrToInt
</li>
<li>RtlLongPtrToInt
</li>
<li>RtlLongLongToInt32
</li>
<li>RtlLongLongToIntPtr
</li>
<li>RtlLong64ToInt
</li>
<li>RtlLong64ToInt32
</li>
<li>RtlInt64ToInt
</li>
<li>RtlInt64ToInt32
</li>
</ul>


