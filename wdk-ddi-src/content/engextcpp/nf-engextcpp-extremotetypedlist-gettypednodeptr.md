---
UID : NF:engextcpp.ExtRemoteTypedList.GetTypedNodePtr
title : ExtRemoteTypedList::GetTypedNodePtr method
author : windows-driver-content
description : The GetTypedNodePtr method returns a pointer to the current list item.
old-location : debugger\extremotetypedlist_gettypednodeptr.htm
old-project : debugger
ms.assetid : 3bf50952-7ac9-4c6b-9318-dd64748de9d2
ms.author : windowsdriverdev
ms.date : 1/19/2018
ms.keywords : GetTypedNodePtr method [Windows Debugging], ExtRemoteTypedList class, GetTypedNodePtr method [Windows Debugging], ExtRemoteTypedList::GetTypedNodePtr, debugger.extremotetypedlist_gettypednodeptr, EngExtCpp_Ref_f007b7c1-89b0-43fa-95e3-792a3272b56d.xml, GetTypedNodePtr, ExtRemoteTypedList, ExtRemoteTypedList class [Windows Debugging], GetTypedNodePtr method
ms.prod : windows-hardware
ms.technology : windows-devices
ms.topic : method
req.header : engextcpp.hpp
req.include-header : Engextcpp.hpp
req.target-type : Desktop
req.target-min-winverclnt : 
req.target-min-winversvr : 
req.kmdf-ver : 
req.umdf-ver : 
req.ddi-compliance : 
req.unicode-ansi : 
req.idl : 
req.max-support : 
req.namespace : 
req.assembly : 
req.type-library : 
req.lib : engextcpp.hpp
req.dll : 
req.irql : 
topictype : 
apitype : 
apilocation : 
apiname : 
product : Windows
targetos : Windows
req.typenames : "*PSILO_DRIVER_CAPABILITIES, SILO_DRIVER_CAPABILITIES"
---


# GetTypedNodePtr method
The <b>GetTypedNodePtr</b> method returns a pointer to the current list item.

## Syntax

````
ExtRemoteTyped GetTypedNodePtr();
````

## Parameters

This function has no parameters.

## Return Value

<b>GetTypedNodePtr</b> returns a typed data description of a pointer to the current list item.


## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows Driver kit version** |  |
| **Target platform** | Desktop |
| **Minimum KMDF version** |  |
| **Minimum UMDF version** |  |
| **Header** | engextcpp.hpp (include Engextcpp.hpp) |
| **Library** |  |
| **IRQL** |  |
| **DDI compliance rules** |  |