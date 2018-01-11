---
UID: NF.wdm.IoCreateSystemThread
title: IoCreateSystemThread function
author: windows-driver-content
description: The IoCreateSystemThread routine creates a system thread that executes in kernel mode, and supplies a handle for the thread.
old-location: kernel\iocreatesystemthread.htm
old-project: kernel
ms.assetid: B2879353-3917-46AA-89CC-A20F0BB78BC4
ms.author: windowsdriverdev
ms.date: 12/15/2017
ms.keywords: IoCreateSystemThread
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCreateSystemThread
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
req.product: Windows 10 or later.
---

# IoCreateSystemThread function



## -description
The <b>IoCreateSystemThread</b> routine creates a system thread that executes in kernel mode, and supplies a handle for the thread.



## -syntax

````
NTSTATUS IoCreateSystemThread(
  _Inout_   PVOID              IoObject,
  _Out_     PHANDLE            ThreadHandle,
  _In_      ULONG              DesiredAccess,
  _In_opt_  POBJECT_ATTRIBUTES ObjectAttributes,
  _In_opt_  HANDLE             ProcessHandle,
  _Out_opt_ PCLIENT_ID         ClientId,
  _In_      PKSTART_ROUTINE    StartRoutine,
  _In_opt_  PVOID              StartContext
);
````


## -parameters

### -param IoObject [in, out]

A pointer to the <a href="kernel.device_object">DEVICE_OBJECT</a> or <a href="kernel.driver_object">DRIVER_OBJECT</a> to associate with          the created thread. <b>IoCreateSystemThread</b> takes a counted reference to this object. The I/O manager later releases this reference when the thread exits. For more information, see Remarks.


### -param ThreadHandle [out]

A pointer to a variable to which the routine writes the kernel handle for the created thread. When the handle is no longer needed, the driver must close the handle by calling the <a href="kernel.zwclose">ZwClose</a> routine.


### -param DesiredAccess [in]

The <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> value that represents the types of access the caller requests to the created thread.


### -param ObjectAttributes [in, optional]

A pointer to an <a href="kernel.object_attributes">OBJECT_ATTRIBUTES</a> structure that specifies the thread object's attributes. The OBJ_PERMANENT, OBJ_EXCLUSIVE, and OBJ_OPENIF attributes are not valid attributes for a thread object. If the caller is not running in the system process context, it must set the OBJ_KERNEL_HANDLE attribute in the <b>OBJECT_ATTRIBUTES</b> structure.


### -param ProcessHandle [in, optional]

An open handle for the process in whose address space the created thread is to run. The caller's thread must have PROCESS_CREATE_THREAD access to this process. If this parameter is <b>NULL</b>, the thread will be created in the initial system process. This parameter should be <b>NULL</b> for a driver-created thread. Use the <b>NtCurrentProcess</b> macro, defined in the Wdm.h header file, to specify the current process.


### -param ClientId [out, optional]

A pointer to a structure to which the routine writes the client identifier for the created thread. This parameter should be <b>NULL</b> for a driver-created thread.


### -param StartRoutine [in]

A pointer to a <a href="kernel.threadstart">ThreadStart</a> routine that is the entry point for the created thread.


### -param StartContext [in, optional]

A context pointer that is passed as the <i>StartContext</i> parameter to the <a href="kernel.threadstart">ThreadStart</a> routine when the created thread starts to run.


## -returns
<b>IoCreateSystemThread</b> returns STATUS_SUCCESS if the new thread was successfully created. Possible return values include the following error status codes.
<dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><i>ProcessHandle</i> is not a valid process handle.
<dl>
<dt><b>STATUS_PROCESS_IS_TERMINATING</b></dt>
</dl>The process specified by <i>ProcessHandle</i> is terminating.
<dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl>Insufficient system resources are available to perform the requested operation.

 


## -remarks
Starting with Windows 8, a driver can call <b>IoCreateSystemThread</b> to create a device-dedicated thread.
     This routine creates a new system thread that has no thread environment block (TEB) or user-mode context, and runs only in kernel mode.

Typically, the driver calls <b>IoCreateSystemThread</b> either when it starts the device, or when the driver's <i>Dispatch</i>Xxx routines start to receive I/O requests. For example, a driver might call this routine to create a thread when a <i>Dispatch</i>Xxx routine receives an asynchronous device control request.

If the <i>ProcessHandle</i> parameter is <b>NULL</b>, the created thread is associated with the system process. Such a thread continues running until either the system is shut down or the thread exits.

Driver routines that run in a process context other than that of the system process must set the OBJ_KERNEL_HANDLE attribute for the <i>ObjectAttributes</i> parameter of <b>IoCreateSystemThread</b>. This attribute restricts the use of the handle returned by <b>IoCreateSystemThread</b> to processes running in kernel mode. Otherwise, the thread handle could be accessed by the process in whose context the driver is running. Drivers can call the <a href="kernel.initializeobjectattributes">InitializeObjectAttributes</a> macro to set the OBJ_KERNEL_HANDLE attribute in the object attributes, as shown in the following code example.

<b>IoCreateSystemThread</b> is similar to the <a href="kernel.pscreatesystemthread">PsCreateSystemThread</a> routine, but has an additional parameter, <i>IoObject</i>, which is a pointer to the caller's driver object or device object. <b>IoCreateSystemThread</b> uses this parameter to ensure that the driver cannot unload while the created thread exists. Before scheduling <i>StartRoutine</i> to run in this thread, <b>IoCreateSystemThread</b> takes a counted reference to the <i>IoObject</i> object. The I/O manager releases this reference after the created thread exits. Thus, this object persists for the lifetime of the created thread.

In contrast to a system thread that is created by the <a href="kernel.pscreatesystemthread">PsCreateSystemThread</a> routine, a thread created by <b>IoCreateSystemThread</b> does not call the <a href="kernel.psterminatesystemthread">PsTerminateSystemThread</a> routine to terminate itself. Instead, the I/O manager calls <b>PsTerminateSystemThread</b> on behalf of the created thread when the thread exits.


## -requirements
<table>
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
Available starting with Windows 8.

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
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
DLL

</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
IRQL

</th>
<td width="70%">
PASSIVE_LEVEL

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a>
</dt>
<dt>
<a href="kernel.device_object">DEVICE_OBJECT</a>
</dt>
<dt>
<a href="kernel.driver_object">DRIVER_OBJECT</a>
</dt>
<dt>
<a href="kernel.initializeobjectattributes">InitializeObjectAttributes</a>
</dt>
<dt>
<a href="kernel.object_attributes">OBJECT_ATTRIBUTES</a>
</dt>
<dt>
<a href="kernel.pscreatesystemthread">PsCreateSystemThread</a>
</dt>
<dt>
<a href="kernel.psterminatesystemthread">PsTerminateSystemThread</a>
</dt>
<dt>
<a href="kernel.threadstart">ThreadStart</a>
</dt>
<dt>
<a href="kernel.zwclose">ZwClose</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoCreateSystemThread routine%20 RELEASE:%20(12/15/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
