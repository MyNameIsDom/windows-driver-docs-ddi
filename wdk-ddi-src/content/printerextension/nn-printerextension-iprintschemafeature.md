---
UID : NN:printerextension.IPrintSchemaFeature
title : IPrintSchemaFeature
author : windows-driver-content
description : Exposes a Print Schema Feature element.
old-location : print\iprintschemafeature_interface.htm
old-project : print
ms.assetid : AAC2A60B-9E70-4809-969A-68783A91B093
ms.author : windowsdriverdev
ms.date : 1/8/2018
ms.keywords : IPrintSchemaTicket2, IPrintSchemaTicket2::GetParameterInitializer, GetParameterInitializer
ms.prod : windows-hardware
ms.technology : windows-devices
ms.topic : interface
req.header : printerextension.h
req.include-header : 
req.target-type : Windows
req.target-min-winverclnt : Windows 8
req.target-min-winversvr : Windows Server 2012
req.kmdf-ver : 
req.umdf-ver : 
req.alt-api : IPrintSchemaFeature
req.alt-loc : Printerextension.h
req.ddi-compliance : 
req.unicode-ansi : 
req.idl : 
req.max-support : 
req.namespace : 
req.assembly : 
req.type-library : 
req.lib : 
req.dll : 
req.irql : 
req.typenames : PrintSchemaSelectionType
req.product : Windows 10 or later.
---

# IPrintSchemaFeature interface

Exposes a Print Schema Feature element.

## Methods

<p>The <b>IPrintSchemaFeature</b> interface has these methods.</p>

| Method | Description |
| ---- |:---- |
| [printerextension.IPrintSchemaFeature.GetOption](nf-printerextension-iprintschemafeature-getoption.md) | Gets the option with the given name. |

## Remarks

You must ensure that each Feature or Option in a PrintTicket or PrintCapabilities XML document has a <i>name</i> attribute specified. This attribute is used to build the <a href="..\printerextension\nn-printerextension-iprintschemaoption.md">IPrintSchemaOption</a> and <b>IPrintSchemaFeature</b> objects. If the <i>name</i> attribute is omitted, the feature or option will not be displayed in the object model, or the Microsoft-provided print preferences experience.

## Requirements
| &nbsp; | &nbsp; |
| ---- |:---- |
| **Windows Driver kit version** |  |
| **Target platform** | Windows |
| **Minimum UMDF version** |  |
| **Header** | printerextension.h |
| **DLL** |  |

    ## See Also

        <dl>
<dt>
<a href="..\printerextension\nn-printerextension-iprintschemadisplayableelement.md">IPrintSchemaDisplayableElement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/AC6434F5-0892-4426-98BB-BC02AD17917B">IPrintSchemaCapabilities::GetFeature</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2E65BDF2-9539-402B-AF19-8CBC84F9C018">IPrintSchemaTicket::GetFeature</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3BD7B8D6-B06F-492F-A73E-DA0799387B2A">IPrintSchemaTicket::GetFeatureByKeyName</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IPrintSchemaFeature interface%20 RELEASE:%20(1/8/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>