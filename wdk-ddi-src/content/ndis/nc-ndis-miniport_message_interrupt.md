---
UID: NC.ndis.MINIPORT_MESSAGE_INTERRUPT
title: MINIPORT_MESSAGE_INTERRUPT
author: windows-driver-content
description: NDIS calls the MiniportMessageInterrupt function when a NIC generates a message-based interrupt.
old-location: netvista\miniportmessageinterrupt.htm
old-project: NetVista
ms.assetid: ec2e6f49-dc40-48e8-96dc-c9440a6662a3
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: RxNameCacheInitialize
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MiniportMessageInterrupt
req.alt-loc: Ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section
---

# MINIPORT_MESSAGE_INTERRUPT callback



## -description
NDIS calls the
   <i>MiniportMessageInterrupt</i> function when a NIC generates a message-based interrupt.



## -prototype

````
MINIPORT_MESSAGE_INTERRUPT MiniportMessageInterrupt;

BOOLEAN MiniportMessageInterrupt(
  _In_  NDIS_HANDLE MiniportInterruptContext,
  _In_  ULONG       MessageId,
  _Out_ PBOOLEAN    QueueDefaultInterruptDpc,
  _Out_ PULONG      TargetProcessors
)
{ ... }
````


## -parameters

### -param MiniportInterruptContext [in]

A handle to a block of interrupt context information. The miniport driver supplied this handle in
     the 
     <i>MiniportInterruptContext</i> parameter that the miniport driver passed to the 
     <a href="netvista.ndismregisterinterruptex">
     NdisMRegisterInterruptEx</a> function.


### -param MessageId [in]

A message-signaled interrupt (MSI) message identifier. 
     <i>MessageId</i> is an index to an 
     <a href="kernel.io_interrupt_message_info_entry">
     IO_INTERRUPT_MESSAGE_INFO_ENTRY</a> structure inside a 
     <a href="kernel.io_interrupt_message_info">
     IO_INTERRUPT_MESSAGE_INFO</a> structure. NDIS passes a pointer to the associated
     <b>IO_INTERRUPT_MESSAGE_INFO</b> structure at the 
     <b>MessageInfoTable</b> member when the driver successfully registers for MSI with the 
     <a href="netvista.ndismregisterinterruptex">NdisMRegisterInterruptEx</a> function.


### -param QueueDefaultInterruptDpc [out]

A pointer to a Boolean variable that the miniport driver sets before returning from this call. A
     miniport driver sets this value to <b>TRUE</b> to indicate that the driver requires a DPC on the default
     (current) CPU. If set to <b>TRUE</b>, NDIS ignores the value of the 
     <i>TargetProcessors</i> parameter. If set to <b>FALSE</b>, NDIS uses the value of the 
     <i>TargetProcessors</i> parameter to schedule DPCs.


### -param TargetProcessors [out]

A bitmask that indicates the target processors for which NDIS should schedule a DPC. This bitmask represents the first 32 processors in processor group 0. Each bit in 
     the bitmask identifies a CPU. If the caller sets bit 0, NDIS schedules a DPC for CPU 0. If the caller sets bit 1, NDIS
     schedules a DPC for CPU 1, and so on. 

<div class="alert"><b>Note</b>  NDIS
     6.20 and later drivers should not use this parameter to schedule DPCs. Instead, they should set this parameter to zero and use the 
     <a href="netvista.ndismqueuedpcex">NdisMQueueDpcEx</a> function to schedule DPCs.</div>
<div> </div>

## -returns
<i>MiniportMessageInterrupt</i> returns <b>TRUE</b> if the underlying NIC generated the interrupt; otherwise, it
     returns <b>FALSE</b>.


## -remarks
Miniport drivers that register for message-signaled interrupts (MSI) support with the 
    <a href="netvista.ndismregisterinterruptex">NdisMRegisterInterruptEx</a> function
    must provide a 
    <i>MiniportMessageInterrupt</i> function.

A miniport driver should do as little work as possible in its 
    <i>MiniportMessageInterrupt</i> function. It should defer I/O operations for the interrupts that the NIC
    generates to the 
    <a href="..\ndis\nc-ndis-miniport_message_interrupt_dpc.md">
    MiniportMessageInterruptDPC</a> function.

When a NIC generates an MSI, NDIS calls the miniport driver's 
    <i>MiniportMessageInterrupt</i> function.

<i>MiniportMessageInterrupt</i> saves required state information about the interrupt and defers as much of
    the I/O processing as possible to the 
    <a href="..\ndis\nc-ndis-miniport_message_interrupt_dpc.md">
    MiniportMessageInterruptDPC</a> function.

If the miniport driver requests deferred procedure calls (DPCs) for a specified message, the miniport
    driver should disable all further interrupts for that message and reenable the interrupts after all the
    DPCs are finished.

The miniport driver should set 
    <i>QueueDefaultInterruptDpc</i> to <b>TRUE</b> to schedule a DPC for the default CPU only. The driver can do
    this, for example, if:

The NIC generated the interrupt to signal the completion of a send operation or any other request
      that doesn't run on other CPUs.

The NIC generated the interrupt to signal received data and the miniport driver cannot process
      received packets in separate DPCs.

The interrupt indicates received packets and the miniport driver can process received packets in
      separate DPCs, but <a href="netvista.ndis_receive_side_scaling2">receive side scaling (RSS)</a> is not enabled for the miniport driver. For more information, see 
      <a href="netvista.oid_gen_receive_scale_capabilities">
      OID_GEN_RECEIVE_SCALE_CAPABILITIES</a> and 
      <a href="netvista.oid_gen_receive_scale_parameters">
      OID_GEN_RECEIVE_SCALE_PARAMETERS</a>.

Receive side scaling is enabled for the miniport driver, and the miniport driver can generate
      different messages on every receive queue.

If a miniport driver processes received packets in separate DPCs, the miniport driver sets the 
    <i>QueueDefaultInterruptDpc</i> parameter to <b>FALSE</b>. The miniport driver should set the 
    <i>TargetProcessors</i> bit for the CPU that is associated with each nonempty receive queue. NDIS will
    schedule a DPC on each of the indicated CPUs in processor group 0.

If 
    <i>MiniportMessageInterrupt</i> shares resources for a specified message, such as NIC registers or state
    variables, with another 
    <i>MiniportXxx</i> function that runs at a lower IRQL, that 
    <i>MiniportXxx</i> function must call the 
    <a href="netvista.ndismsynchronizewithinterruptex">
    NdisMSynchronizeWithInterruptEx</a> function. This ensures that the driver's 
    <a href="netvista.miniportsynchronizemessageinterrupt">MiniportSynchronizeMessageInterrupt</a> function accesses the shared resources in a synchronized and
    multiprocessor-safe manner.

A miniport driver can call the 
    <a href="netvista.ndismderegisterinterruptex">
    NdisMDeregisterInterruptEx</a> function from its 
    <a href="..\ndis\nc-ndis-miniport_initialize.md">MiniportInitializeEx</a> or 
    <a href="..\ndis\nc-ndis-miniport_halt.md">MiniportHaltEx</a> function to release resources that it allocated with 
    <a href="netvista.ndismregisterinterruptex">NdisMRegisterInterruptEx</a>. After 
    <b>NdisMDeregisterInterruptEx</b> returns, NDIS does not call a miniport driver's 
    <i>MiniportMessageInterrupt</i> or 
    <a href="..\ndis\nc-ndis-miniport_message_interrupt_dpc.md">MiniportMessageInterruptDPC</a> function.

NDIS calls 
    <i>MiniportMessageInterrupt</i> at the DIRQL of the MSI that the miniport driver registered in a previous
    call to 
    <a href="netvista.ndismregisterinterruptex">NdisMRegisterInterruptEx</a>. Therefore, 
    <i>MiniportMessageInterrupt</i> must call the subset of the NDIS functions, such as the 
    <b>NdisRaw<i>Xxx</i></b> or 
    <b>NdisRead/WriteRegister<i>Xxx</i></b> functions, that are safe to call at any IRQL.

To define a <i>MiniportMessageInterrupt</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="https://msdn.microsoft.com/2F3549EF-B50F-455A-BDC7-1F67782B8DCA">Code Analysis for Drivers</a>, <a href="https://msdn.microsoft.com/74feeb16-387c-4796-987a-aff3fb79b556">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.

For example, to define a <i>MiniportMessageInterrupt</i> function that is named "MyMessageInterrupt", use the <b>MINIPORT_MESSAGE_INTERRUPT</b> type as shown in this code example:

Then, implement your function as follows:

The <b>MINIPORT_MESSAGE_INTERRUPT</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>MINIPORT_MESSAGE_INTERRUPT</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="https://msdn.microsoft.com/232c4272-0bf0-4a4e-9560-3bceeca8a3e3">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. 


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported in NDIS 6.0 and later.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
See Remarks section

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="kernel.io_interrupt_message_info">IO_INTERRUPT_MESSAGE_INFO</a>
</dt>
<dt>
<a href="kernel.io_interrupt_message_info_entry">
   IO_INTERRUPT_MESSAGE_INFO_ENTRY</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-miniport_halt.md">MiniportHaltEx</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-miniport_initialize.md">MiniportInitializeEx</a>
</dt>
<dt>
<a href="..\ndis\nc-ndis-miniport_message_interrupt_dpc.md">MiniportMessageInterruptDPC</a>
</dt>
<dt>
<a href="netvista.miniportsynchronizemessageinterrupt">MiniportSynchronizeMessageInterrupt</a>
</dt>
<dt>
<a href="netvista.ndis_miniport_interrupt_characteristics">
   NDIS_MINIPORT_INTERRUPT_CHARACTERISTICS</a>
</dt>
<dt>
<a href="netvista.ndismderegisterinterruptex">NdisMDeregisterInterruptEx</a>
</dt>
<dt>
<a href="netvista.ndismqueuedpcex">NdisMQueueDpcEx</a>
</dt>
<dt>
<a href="netvista.ndismregisterinterruptex">NdisMRegisterInterruptEx</a>
</dt>
<dt>
<a href="netvista.ndismsynchronizewithinterruptex">
   NdisMSynchronizeWithInterruptEx</a>
</dt>
<dt>
<a href="netvista.oid_gen_receive_scale_capabilities">
   OID_GEN_RECEIVE_SCALE_CAPABILITIES</a>
</dt>
<dt>
<a href="netvista.oid_gen_receive_scale_parameters">
   OID_GEN_RECEIVE_SCALE_PARAMETERS</a>
</dt>
<dt>
<a href="netvista.ndis_receive_side_scaling2">Receive Side Scaling (RSS)</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [NetVista\netvista]:%20MINIPORT_MESSAGE_INTERRUPT callback function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
