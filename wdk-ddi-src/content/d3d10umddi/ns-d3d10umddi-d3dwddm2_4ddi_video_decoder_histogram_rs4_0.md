---
UID: NS:d3d10umddi.D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0
title: D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0
author: windows-driver-content
description:
ms.assetid: 12eac5ab-18cb-4274-aa0a-1ee5fef2218f
ms.author: windowsdriverdev
ms.date:
ms.topic: struct
ms.prod: windows-hardware
ms.technology: windows-devices
ms.keywords: D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0, D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0,
req.header: d3d10umddi.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.ddi-compliance:
req.unicode-ansi:
req.max-support:
req.typenames: D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0
topictype:
-	apiref
apitype:
-	HeaderDef
apilocation:
-	d3d10umddi.h
apiname:
-	D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0
product: Windows
targetos: Windows
---

# D3DWDDM2_4DDI_VIDEO_DECODER_HISTOGRAM_RS4_0 structure

## -description

Contains decode histogram output buffer information such as decode profile, resolution, and format.

## -struct-fields

### -field Offset

The offset location in hBuffer to write the component histogram.

### -field hBuffer

The target buffer for hardware to write the components histogram. Set to a nullptr when the component histogram is disabled.

## -remarks

## -see-also