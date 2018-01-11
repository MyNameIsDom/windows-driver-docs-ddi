---
UID: NF.fltkernel.FltCreateNamedPipeFile
title: FltCreateNamedPipeFile function
author: windows-driver-content
description: Minifilter drivers call FltCreateNamedPipeFile to create a new pipe or open an existing pipe.
old-location: ifsk\fltcreatenamedpipefile.htm
old-project: ifsk
ms.assetid: F4F3A591-B4BE-4367-A76A-820552F9B3B5
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: FltCreateNamedPipeFile
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: fltkernel.h
req.include-header: FltKernel.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltCreateNamedPipeFile
req.alt-loc: Fltmgr.lib,Fltmgr.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fltmgr.lib
req.dll: 
req.irql: PASSIVE_LEVEL
---

# FltCreateNamedPipeFile function



## -description
Minifilter drivers call <b>FltCreateNamedPipeFile</b> to create a new pipe or open an existing pipe.  



## -syntax

````
NTSTATUS FltCreateNamedPipeFile(
  _In_      PFLT_FILTER               Filter,
  _In_opt_  PFLT_INSTANCE             Instance,
  _Out_     PHANDLE                   FileHandle,
  _Out_opt_ PFILE_OBJECT              *FileObject,
  _In_      ACCESS_MASK               DesiredAccess,
  _In_      POBJECT_ATTRIBUTES        ObjectAttributes,
  _Out_     PIO_STATUS_BLOCK          IoStatusBlock,
  _In_      ULONG                     ShareAccess,
  _In_      ULONG                     CreateDisposition,
  _In_      ULONG                     CreateOptions,
  _In_      ULONG                     NamedPipeType,
  _In_      ULONG                     ReadMode,
  _In_      ULONG                     CompletionMode,
  _In_      ULONG                     MaximumInstances,
  _In_      ULONG                     InBoundQuota,
  _In_      ULONG                     OutBoundQuota,
  _In_opt_  PLARGE_INTEGER            DefaultTimeout,
  _In_opt_  PIO_DRIVER_CREATE_CONTEXT DriverContext
);
````


## -parameters

### -param Filter [in]

An opaque filter pointer for the caller. 


### -param Instance [in, optional]

An opaque instance pointer for the minifilter driver instance that the create request is to be sent to. The instance must be attached to the volume for the named pipe file system. This parameter is optional and can be <b>NULL</b>. If this parameter is <b>NULL</b>, the request is sent to the device object at the top of the file system driver stack for the volume. If it is non-<b>NULL</b>, the request is sent only to minifilter driver instances that are attached below the specified instance. 


### -param FileHandle [out]

A pointer to a caller-allocated variable that receives the file handle if the call to  <b>FltCreateNamedPipeFile</b> is successful. 


### -param FileObject [out, optional]

A pointer to a caller-allocated variable that receives the file object pointer if the call to <b>FltCreateNamedPipeFile</b> is successful. This parameter is optional and can be <b>NULL</b>. 


### -param DesiredAccess [in]

A bitmask of flags that specify the type of access that the caller requires to the file or directory. The set of system-defined <i>DesiredAccess</i> flags determines the following specific access rights for file objects. 

<table>
<tr>
<th>DesiredAccess Flags</th>
<th>Meaning</th>
</tr>
<tr>
<td>
FILE_READ_DATA

</td>
<td>
Data can be read from the named pipe.

</td>
</tr>
<tr>
<td>
FILE_READ_ATTRIBUTES

</td>
<td>
<i>FileAttributes</i> flags can be read.  For additional information, see the table of valid flag values in the <i>FileAttributes</i> parameter of <a href="ifsk.fltcreatefileex2">FltCreateFileEx2</a>.

</td>
</tr>
<tr>
<td>
READ_CONTROL

</td>
<td>
The access control list (<a href="ifsk.acl">ACL</a>) and ownership information associated with the named pipe can be read.

</td>
</tr>
<tr>
<td>
FILE_WRITE_DATA

</td>
<td>
Data can be written to the named pipe.

</td>
</tr>
<tr>
<td>
FILE_WRITE_ATTRIBUTES

</td>
<td>
<i>FileAttributes</i> flags can be written.

</td>
</tr>
<tr>
<td>
FILE_APPEND_DATA

</td>
<td>
Data can be appended to the file.

</td>
</tr>
<tr>
<td>
WRITE_DAC 

</td>
<td>
The discretionary access control list (<a href="ifsk.acl">DACL</a>) associated with the named pipe can be written.

</td>
</tr>
<tr>
<td>
WRITE_OWNER 

</td>
<td>
Ownership information associated with the named pipe can be written.

</td>
</tr>
<tr>
<td>
ACCESS_SYSTEM_SECURITY

</td>
<td>
The caller will have write access to the named pipe's SACL

</td>
</tr>
<tr>
<td>
SYNCHRONIZE

</td>
<td>
The caller can synchronize the completion of an I/O operation by waiting for the returned <i>FileHandle</i> to be set to the Signaled state. This flag must be set if the <i>CreateOptions</i> FILE_SYNCHRONOUS_IO_ALERT or FILE_SYNCHRONOUS_IO_NONALERT flag is set. 

</td>
</tr>
</table>
 

Alternatively, for any file object that does not represent a directory, you can specify one or more of the following generic <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> flags. (The STANDARD_RIGHTS_<i>XXX</i> flags are predefined system values that are used to enforce security on system objects.) You can also combine these generic flags with additional flags from the preceding table. 

<table>
<tr>
<th>DesiredAccess to File Values</th>
<th>Maps to <i>DesiredAccess</i> Flags</th>
</tr>
<tr>
<td>
GENERIC_READ

</td>
<td>
STANDARD_RIGHTS_READ, FILE_READ_DATA, and SYNCHRONIZE. 

</td>
</tr>
<tr>
<td>
GENERIC_WRITE

</td>
<td>
STANDARD_RIGHTS_WRITE, FILE_WRITE_DATA, FILE_APPEND_DATA, and SYNCHRONIZE. 

</td>
</tr>
</table>
 


### -param ObjectAttributes [in]

A pointer to an opaque <a href="kernel.object_attributes">OBJECT_ATTRIBUTES</a> structure that is already initialized with <a href="kernel.initializeobjectattributes">InitializeObjectAttributes</a>. If the caller is running in the system process context, this parameter can be <b>NULL</b>. Otherwise, the caller must set the OBJ_KERNEL_HANDLE attribute in the call to <b>InitializeObjectAttributes</b>. Members of this structure for a file object are listed in the following table. 

<table>
<tr>
<th>Member</th>
<th>Value</th>
</tr>
<tr>
<td>
<b>ULONG </b><b>Length</b>

</td>
<td>
The number of bytes of data that are contained in the structure pointed to by <i>ObjectAttributes</i>. This value must be at least <b>sizeof</b>(OBJECT_ATTRIBUTES).

</td>
</tr>
<tr>
<td>
<b>PUNICODE_STRING </b><b>ObjectName</b>

</td>
<td>
A pointer to a <a href="kernel.unicode_string">UNICODE_STRING</a> structure that contains the name of the pipe to be created or opened. This name must be a fully qualified file specification or the name of a device object unless it is the name of a file relative to the directory specified by <b>RootDirectory</b>. For example, "\Device\NamedPipe\mypipe" or "\??\pipe\mypipe" could both be valid file specifications. (Note: "\??" replaces "\DosDevices" as the name of the Win32 object namespace. "\DosDevices" still works, but "\??" is translated faster by the object manager.)

</td>
</tr>
<tr>
<td>
<b>HANDLE </b><b>RootDirectory</b>

</td>
<td>
An optional handle to a directory, obtained by a preceding call to <a href="ifsk.fltcreatefileex2">FltCreateFileEx2</a>. If this value is <b>NULL</b>, the <i>ObjectName</i>member must be a fully qualified file specification that includes the full path to the target pipe. If this value is non-<b>NULL</b>, the <i>ObjectName</i> member specifies a pipe name that is relative to this directory.

</td>
</tr>
<tr>
<td>
<b>PSECURITY_DESCRIPTOR </b><b>SecurityDescriptor</b>

</td>
<td>
An optional security descriptor (<a href="ifsk.security_descriptor">SECURITY_DESCRIPTOR</a>) to be applied to a pipe. <a href="ifsk.acl">ACLs</a> specified by such a security descriptor are only applied to the pipe when it is created. If the value is <b>NULL</b> when a pipe is created, the ACL placed on the pipe is dependant on the named pipe file system and may allow a client with any access to create an instance.

</td>
</tr>
<tr>
<td>
<b>ULONG </b><b>Attributes</b>

</td>
<td>
A set of flags that controls the file object attributes. If the caller is running in the system process context, this parameter can be zero. Otherwise, the caller must set the OBJ_KERNEL_HANDLE flag. The caller can also optionally set the OBJ_CASE_INSENSITIVE flag, which indicates that name-lookup code should ignore the case of <i>ObjectName</i> rather than performing an exact-match search. 

</td>
</tr>
</table>
 


### -param IoStatusBlock [out]

A pointer to an <a href="kernel.io_status_block">IO_STATUS_BLOCK</a> structure that receives the final completion status and information about the requested operation. On return from <b>FltCreateNamedPipeFile</b>, the <b>Information</b> member of the variable contains one of the following values:

<dl>
<dd>
FILE_CREATED

</dd>
<dd>
FILE_OPENED

</dd>
</dl>

### -param ShareAccess [in]

The type of share access to the file that the caller requires as one or a combination of the following flags. For the greatest chance of avoiding sharing violation errors, specify all of the following share access flags. 

<table>
<tr>
<th><i>ShareAccess</i> flags</th>
<th>Meaning</th>
</tr>
<tr>
<td>
FILE_SHARE_READ

</td>
<td>
The file can be opened for read access by other threads' calls to <b>FltCreateNamedPipeFile</b>.

</td>
</tr>
<tr>
<td>
FILE_SHARE_WRITE

</td>
<td>
The file can be opened for write access by other threads' calls to <b>FltCreateNamedPipeFile</b>.

</td>
</tr>
</table>
 


### -param CreateDisposition [in]

A value that determines the action to be taken, depending on whether the file already exists. The value can be any of those described in the following table. 

<table>
<tr>
<th><i>CreateDisposition</i> values</th>
<th>Meaning</th>
</tr>
<tr>
<td>
FILE_CREATE 

</td>
<td>
If the file already exists, fail the request and do not create or open the specified file. If it does not, create the  file.

</td>
</tr>
<tr>
<td>
FILE_OPEN 

</td>
<td>
If the file already exists, open it instead of creating a new file. If it does not, fail the request and do not create a new file.

</td>
</tr>
<tr>
<td>
FILE_OPEN_IF

</td>
<td>
If the file already exists, open it. If it does not, create the file.

</td>
</tr>
</table>
 


### -param CreateOptions [in]

The options to be applied when creating or opening the pipe, as a compatible combination of the following flags. 

<table>
<tr>
<th><i>CreateOptions</i> flags</th>
<th>Meaning</th>
</tr>
<tr>
<td>
FILE_WRITE_THROUGH

</td>
<td>
System services, pipe systems, and drivers that write data to the pipe must actually transfer the data into the pipe before any requested write operation is considered complete. This flag is automatically set if the <i>CreateOptions</i> flag FILE_NO_INTERMEDIATE_BUFFERING is set.

</td>
</tr>
<tr>
<td>
FILE_SYNCHRONOUS_IO_ALERT

</td>
<td>
All operations on the pipe are performed synchronously. Any wait on behalf of the caller is subject to premature termination from alerts. This flag also causes the I/O system to maintain the pipe position context. If this flag is set, the <i>DesiredAccess</i> SYNCHRONIZE flag also must be set so that the I/O Manager uses the file object as a synchronization object. 

</td>
</tr>
<tr>
<td>
FILE_SYNCHRONOUS_IO_NONALERT

</td>
<td>
All operations on the pipe are performed synchronously. Waits in the system to synchronize I/O queuing and completion are not subject to alerts. This flag also causes the I/O system to maintain the file position context. If this flag is set, the <i>DesiredAccess</i> SYNCHRONIZE flag also must be set so that the I/O Manager uses the file object as a synchronization object.

</td>
</tr>
</table>
 


### -param NamedPipeType [in]

The mode to read from the pipe.

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>

### -param FILE_PIPE_BYTE_STREAM_TYPE

</td>
<td width="60%">
The data is written to the pipe as a stream of bytes. To use this type, <i>ReadMode</i> must not be FILE_PIPE_MESSAGE_MODE.

</td>
</tr>
<tr>

### -param FILE_PIPE_MESSAGE_TYPE

</td>
<td width="60%">
The data is written to the pipe as a message.

</td>
</tr>
</table>
 


### -param ReadMode [in]

The mode to read from the pipe.

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>

### -param FILE_PIPE_BYTE_STREAM_MODE

</td>
<td width="60%">
The pipe data is read as a stream of bytes.

</td>
</tr>
<tr>

### -param FILE_PIPE_MESSAGE_MODE

</td>
<td width="60%">
The pipe data is read as messages. To use this mode, <i>NamedPipeType</i> must be  FILE_PIPE_MESSAGE_TYPE.

</td>
</tr>
</table>
 


### -param CompletionMode [in]

The completion mode for pipe reads and writes.

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>

### -param FILE_PIPE_QUEUE_COMPLETION

</td>
<td width="60%">
The pipe read and write requests are  queued and can block until completed.

</td>
</tr>
<tr>

### -param FILE_PIPE_COMPLETE_OPERATION

</td>
<td width="60%">
The pipe read and write requests are completed immediately.

</td>
</tr>
</table>
 


### -param MaximumInstances [in]

The maximum number of instances allowed for this named pipe.


### -param InBoundQuota [in]

The number of bytes to reserve for the input buffer.


### -param OutBoundQuota [in]

The number of bytes to reserve for the output buffer.


### -param DefaultTimeout [in, optional]

The default timeout in 100-nanosecond increments. This value is expressed as a negative integer. For example, 250 milliseconds is specified as –10 * 1000 * 250.


### -param DriverContext [in, optional]

An optional pointer to an <a href="ifsk.io_driver_create_context">IO_DRIVER_CREATE_CONTEXT</a> structure already initialized by <a href="ifsk.ioinitializedrivercreatecontext">IoInitializeDriverCreateContext</a>.


## -returns
<b>FltCreateNamedPipeFile</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value such as one of the following. 
<dl>
<dt><b>STATUS_FLT_DELETING_OBJECT</b></dt>
</dl>The filter or instance specified in the <i>Filter</i> or <i>Instance</i> parameters is being torn down. This status code can be received if the open request crosses a volume mount point and the <i>Instance</i> parameter is non-<b>NULL</b>. This is an error code. 
<dl>
<dt><b>STATUS_OBJECT_PATH_SYNTAX_BAD</b></dt>
</dl>The <i>ObjectAttributes</i> parameter did not contain a <b>RootDirectory</b> member, but the <b>ObjectName</b> member in the OBJECT_ATTRIBUTES structure was an empty string or did not contain an OBJECT_NAME_PATH_SEPARATOR character. This error code indicates incorrect syntax for the object path. 

 


## -remarks
The <b>FltCreateNamedPipeFile</b> function allows minifilter drivers to create or open pipe instances. This is useful for creating virtual pipes or for creating pipe unions for multiplexing I/O.

The <i>instance</i> parameter is either <b> NULL</b> or is previously set by attaching to the named pipe volume. A volume pointer is obtained by passing "\Device\NamedPipe" as the volume name to <a href="ifsk.fltgetvolumefromname">FltGetVolumeFromName</a>.

To specify an extra create parameter (ECP) as part of a create operation, initialize the <b>ExtraCreateParameter</b> member of the <a href="ifsk.io_driver_create_context">IO_DRIVER_CREATE_CONTEXT</a> structure with the <a href="ifsk.fltallocateextracreateparameterlist">FltAllocateExtraCreateParameterList</a> routine.  If ECPs are used, they must be allocated, initialized, and freed using their associated support routines.  Upon returning from the call of <b>FltCreateNamedPipeFile</b>, the ECP list is unchanged and may be passed to additional calls of <b>FltCreateNamedPipeFile</b> for other create operations.  The ECP list structure is not automatically deallocated. The caller of <b>FltCreateNamedPipeFile</b> must deallocate this structure by calling the <a href="ifsk.fltfreeextracreateparameterlist">FltFreeExtraCreateParameterList</a> routine.


     If <i>Instance</i> is not <b>NULL</b>, the create request from <b>FltCreateNamedPipeFile</b> is sent only to the instances attached below the specified minifilter driver instance and to the named pipe file system. The specified instance and the instances attached above it do not receive the create request. If no instance is specified, the request goes to the top of the stack and is received by all instances and the named pipe file system.


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
Available in Windows 8.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include FltKernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
Library

</th>
<td width="70%">
<dl>
<dt>Fltmgr.lib</dt>
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
<a href="ifsk.fltfreeextracreateparameterlist">FltFreeExtraCreateParameterList</a>
</dt>
<dt>
<a href="ifsk.fltallocateextracreateparameterlist">FltAllocateExtraCreateParameterList</a>
</dt>
<dt>
<a href="kernel.initializeobjectattributes">InitializeObjectAttributes</a>
</dt>
<dt>
<a href="ifsk.io_driver_create_context">IO_DRIVER_CREATE_CONTEXT</a>
</dt>
<dt>
<a href="ifsk.ioinitializedrivercreatecontext">IoInitializeDriverCreateContext</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltCreateNamedPipeFile function%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
