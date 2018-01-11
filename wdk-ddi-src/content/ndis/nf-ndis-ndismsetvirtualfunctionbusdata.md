---
UID: NF.ndis.NdisMSetVirtualFunctionBusData
title: NdisMSetVirtualFunctionBusData function
author: windows-driver-content
description: A miniport driver calls the NdisMSetVirtualFunctionBusData function to write data to the PCI Express (PCIe) configuration space of a Virtual Function (VF) on the network adapter.
old-location: netvista\ndismsetvirtualfunctionbusdata.htm
old-project: NetVista
ms.assetid: 74c6789e-22a6-42e9-bc14-8b9f93da668b
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: NdisMSetVirtualFunctionBusData
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: None supported,Supported in NDIS 6.30 and later.
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMSetVirtualFunctionBusData
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
---

# NdisMSetVirtualFunctionBusData function



## -description
A miniport driver calls the <b>NdisMSetVirtualFunctionBusData</b> function to write data to the PCI  Express (PCIe) configuration space of a Virtual Function (VF) on the network adapter. 



## -syntax

````
ULONG NdisMSetVirtualFunctionBusData(
  _In_ NDIS_HANDLE            NdisMiniportHandle,
  _In_ NDIS_SRIOV_FUNCTION_ID VFId,
  _In_ PVOID                  Buffer,
  _In_ ULONG                  Offset,
  _In_ ULONG                  Length
);
````


## -parameters

### -param NdisMiniportHandle [in]

The network adapter handle that NDIS passed to the 
     <i>MiniportAdapterHandle</i> parameter of 
     <a href="..\ndis\nc-ndis-miniport_initialize.md">MiniportInitializeEx</a>.


### -param VFId [in]

The identifier of the VF to which data is written to its  PCI configuration space.


### -param Buffer [in]

A pointer to a buffer that contains the data to be written to the PCI configuration space.


### -param Offset [in]

The offset, in units of bytes, in the PCI configuration space to which data is written.




### -param Length [in]

The length, in units of bytes, of the data to be written.


## -returns
<b>NdisMSetVirtualFunctionBusData</b> returns the number of bytes written to the PCI configuration space. If the write operation fails, <b>NdisMSetVirtualFunctionBusData</b> returns zero.


## -remarks
The PF miniport driver typically calls <b>NdisMSetVirtualFunctionBusData</b> when it handles an OID method request of  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451925">OID_SRIOV_WRITE_VF_CONFIG_SPACE</a>.  
However, the driver can call this function any time after virtualization has been enabled on the network adapter through a call to <a href="netvista.ndismenablevirtualization">NdisMEnableVirtualization</a>.

For more information about backchannel communication within the single root I/O virtualization (SR-IOV) interface, see <a href="netvista.sr_iov_pf_vf_backchannel_communication">SR-IOV PF/VF Backchannel Communication</a>.

For more information about the SR-IOV interface, see 	<a href="netvista.overview_of_single_root_i_o_virtualization__sr-iov_">Overview of Single Root I/O Virtualization (SR-IOV)</a>.

If an independent hardware vendor (IHV) provides a virtual bus driver (VBD) as part of its SR-IOV <a href="devinst.driver_packages">driver package</a>, its miniport driver must not call <b>NdisMSetVirtualFunctionBusData</b>. Instead, the driver must interface with the VBD through a private communication channel, and request that the VBD call <a href="..\wdm\nc-wdm-set_virtual_device_data.md">SetVirtualFunctionData</a>. This function is exposed from the <a href="kernel.guid_pci_virtualization_interface">GUID_PCI_VIRTUALIZATION_INTERFACE</a> interface that is supported by the underlying PCI bus driver.

The VBD that runs in the Hyper-V parent partition's management operating system can query the <a href="kernel.guid_pci_virtualization_interface">GUID_PCI_VIRTUALIZATION_INTERFACE</a> interface by issuing an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551687">IRP_MN_QUERY_INTERFACE</a> request to its physical device object (PDO) on the PCI bus. This request must be made from IRQL = PASSIVE_LEVEL. In this request, the driver must  set the <i>InterfaceType</i> parameter to GUID_PCI_VIRTUALIZATION_INTERFACE.


## -requirements
<table>
<tr>
<th width="30%">
Minimum supported client

</th>
<td width="70%">
None supported

</td>
</tr>
<tr>
<th width="30%">
Minimum supported server

</th>
<td width="70%">
Windows Server 2012

</td>
</tr>
<tr>
<th width="30%">
Target platform

</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Supported in NDIS 6.30 and later.

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
Library

</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
&lt;= DISPATCH_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt><b></b></dt>
<dt>
<a href="kernel.guid_pci_virtualization_interface">GUID_PCI_VIRTUALIZATION_INTERFACE</a>
</dt>
<dt>
<a href="netvista.ndismenablevirtualization">NdisMEnableVirtualization</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451814">OID_NIC_SWITCH_ALLOCATE_VF</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451925">OID_SRIOV_WRITE_VF_CONFIG_SPACE</a>
</dt>
<dt>
<a href="..\wdm\nc-wdm-set_virtual_device_data.md">SetVirtualFunctionData</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [NetVista\netvista]:%20NdisMSetVirtualFunctionBusData function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
