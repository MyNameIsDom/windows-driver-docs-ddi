---
UID: NC.dot11wdi.MINIPORT_WDI_RX_GET_MPDUS
title: MINIPORT_WDI_RX_GET_MPDUS
author: windows-driver-content
description: The MiniportWdiRxGetMpdus handler function returns a NET_BUFFER_LIST chain. Each NET_BUFFER_LIST represents one MPDU.
old-location: netvista\miniportwdirxgetmpdus.htm
old-project: NetVista
ms.assetid: 195F4143-4889-4788-BAF5-2F1ED6E4E50A
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _SYNTH_STATS, *PSYNTH_STATS, SYNTH_STATS, PSYNTH_STATS
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: dot11wdi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MiniportWdiRxGetMpdus
req.alt-loc: dot11wdi.h
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

# MINIPORT_WDI_RX_GET_MPDUS callback



## -description
The 
  MiniportWdiRxGetMpdus handler function returns a <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> chain. Each NET_BUFFER_LIST represents one MPDU.

This is a WDI miniport handler inside <a href="netvista.ndis_miniport_wdi_data_handlers">NDIS_MINIPORT_WDI_DATA_HANDLERS</a>.



## -prototype

````
MINIPORT_WDI_RX_GET_MPDUS MiniportWdiRxGetMpdus;

VOID MiniportWdiRxGetMpdus(
  _In_  TAL_TXRX_HANDLE  MiniportTalTxRxContext,
  _In_  WDI_PEER_ID      PeerId,
  _In_  WDI_EXTENDED_TID ExTid,
  _Out_ PNET_BUFFER_LIST *ppNBL
)
{ ... }
````


## -parameters

### -param MiniportTalTxRxContext [in]

TAL device handle returned by the IHV miniport in <a href="..\dot11wdi\nc-dot11wdi-miniport_wdi_tal_txrx_initialize.md">MiniportWdiTalTxRxInitialize</a>.


### -param PeerId [in]

The peer ID.


### -param ExTid [in]

The extended TID.


### -param ppNBL [out]

Pointer to a pointer to a <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> chain from the IHV miniport.


## -returns
This callback function does not return a value.


## -remarks
If <i>PeerId</i> and <i>ExTid</i> are not wildcards (for example, <i>PeerId</i> is not equal to 0xFFFF, <i>ExTid</i> is not equal to 31), all MPDUs in the chain are of the same peer ID and TID (in this case, TID is a valid 802.11 TID).

Each <a href="netvista.net_buffer_list">NET_BUFFER_LIST</a> points to <a href="netvista.net_buffer">NET_BUFFER</a> structures. Each NET_BUFFER structure represents one MSDU.

If an MPDU has an MSDU fragment as payload and defragmentation is not offloaded to target/TAL (or  host-implemented FIPS mode is enabled), the corresponding NET_BUFFER_LIST has one NET_BUFFER that describes the MSDU fragment.

The data offset of each NET_BUFFER must be set to the start of the MAC header.

To define a MiniportWdiRxGetMpdus function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="https://msdn.microsoft.com/2F3549EF-B50F-455A-BDC7-1F67782B8DCA">Code Analysis for Drivers</a>, <a href="https://msdn.microsoft.com/74feeb16-387c-4796-987a-aff3fb79b556">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.

For example, to define a MiniportWdiRxGetMpdus function that is named "MyRxGetMpdus", use the <b>MINIPORT_WDI_RX_GET_MPDUS</b> type as shown in this code example:

Then, implement your function as follows:

The <b>MINIPORT_WDI_RX_GET_MPDUS</b> function type is defined in the dot11wdi.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>MINIPORT_WDI_RX_GET_MPDUS</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="https://msdn.microsoft.com/232c4272-0bf0-4a4e-9560-3bceeca8a3e3">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>.


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
Windows 10

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2016

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Dot11wdi.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="netvista.ndis_miniport_wdi_data_handlers">NDIS_MINIPORT_WDI_DATA_HANDLERS</a>
</dt>
<dt>
<a href="netvista.net_buffer">NET_BUFFER</a>
</dt>
<dt>
<a href="netvista.net_buffer_list">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt297625">TAL_TXRX_HANDLE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt297640">WDI_EXTENDED_TID</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt297658">WDI_PEER_ID</a>
</dt>
<dt>
<a href="netvista.wdi_rx_path">WDI RX path</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [NetVista\netvista]:%20MINIPORT_WDI_RX_GET_MPDUS callback function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
