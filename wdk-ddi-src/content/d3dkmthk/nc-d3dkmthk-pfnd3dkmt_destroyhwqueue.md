---
UID: NC:d3dkmthk.PFND3DKMT_DESTROYHWQUEUE
title: PFND3DKMT_DESTROYHWQUEUE
author: windows-driver-content
description:
ms.assetid: 4ac646f8-e8c2-4682-bbab-0e91a782e59a
ms.author: windowsdriverdev
ms.date:
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3dkmthk.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.irql:
req.ddi-compliance:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library:
topictype:
-	apiref
apitype:
-	UserDefined
apilocation:
-	d3dkmthk.h
apiname:
-	PFND3DKMT_DESTROYHWQUEUE
product: Windows
targetos: Windows
---

# PFND3DKMT_DESTROYHWQUEUE callback function

## -description

Implemented by the client driver to destroy a hardware queue.

## -prototype

```
//Declaration

PFND3DKMT_DESTROYHWQUEUE Pfnd3dkmtDestroyhwqueue;

// Definition

NTSTATUS Pfnd3dkmtDestroyhwqueue
(
	CONST D3DKMT_DESTROYHWQUEUE *
)
{...}

PFND3DKMT_DESTROYHWQUEUE


```

## -parameters

### -param D3DKMT_DESTROYHWQUEUE *

Pointer to a [D3DKMT_DESTROYHWQUEUE](ns-d3dkmthk-_d3dkmt_destroyhwqueue.md) structure that contains the information needed to destroy a hardware queue.

## -returns

Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code.

## -remarks

Register your implementation of this callback function by setting the appropriate member of [D3DKMT_DESTROYHWQUEUE](ns-d3dkmthk-_d3dkmt_destroyhwqueue.md) and then calling PfnD3dkmtDestroyHwQueue.

