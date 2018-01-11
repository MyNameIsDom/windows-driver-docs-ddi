---
UID: NF.ntifs.FsRtlCancellableWaitForMultipleObjects
title: FsRtlCancellableWaitForMultipleObjects function
author: windows-driver-content
description: The FsRtlCancellableWaitForMultipleObjects routine executes a cancelable wait operation (a wait that can be terminated) on one or more dispatcher objects.
old-location: ifsk\fsrtlcancellablewaitformultipleobjects.htm
old-project: ifsk
ms.assetid: 9fb5805c-bb12-41ba-8c72-526b4193b6b5
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: FsRtlCancellableWaitForMultipleObjects
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FsRtlCancellableWaitForMultipleObjects
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
req.irql: See Remarks section.
---

# FsRtlCancellableWaitForMultipleObjects function



## -description
The <b>FsRtlCancellableWaitForMultipleObjects</b> routine executes a cancelable wait operation (a wait that can be terminated) on one or more dispatcher objects.



## -syntax

````
NTSTATUS  FsRtlCancellableWaitForMultipleObjects(
  _In_     ULONG          Count,
  _In_     PVOID          ObjectArray,
  _In_     WAIT_TYPE      WaitType,
  _In_opt_ PLARGE_INTEGER Timeout,
  _In_opt_ PKWAIT_BLOCK   WaitBlockArray,
  _In_opt_ PIRP           Irp
);
````


## -parameters

### -param Count [in]

The number of objects to be waited on.


### -param ObjectArray [in]

A pointer to an array of pointers to dispatcher objects (events, mutexes, semaphores, threads, and timers) for which the caller supplies the storage.


### -param WaitType [in]

Either <b>WaitAll</b>, which indicates that all of the specified objects must attain a signaled state before the wait is satisfied; or <b>WaitAny</b>, which indicates that any one of the objects must attain a signaled state before the wait is satisfied.


### -param Timeout [in, optional]

A pointer to an optional time-out value. This parameter specifies the absolute or relative time, in 100 nanosecond units, at which the wait is to be completed.

If <i>Timeout </i>points to a zero value (that is, <i>*Timeout</i> == 0), the routine returns without waiting. If the caller supplies a <b>NULL</b> pointer (that is, <i>Timeout</i> == <b>NULL</b>), the routine waits indefinitely until any or all of the dispatcher objects are set to the signaled state.

A positive value specifies an absolute time, relative to January 1, 1601. A negative value specifies an interval relative to the current time. Absolute expiration times track any changes in the system time; relative expiration times are not affected by system time changes. 

If <i>Timeout</i> is specified, the wait will be automatically satisfied if none of the specified wait conditions are met when the given interval expires.

A time-out value of zero (that is, <i>*Timeout</i> == 0) allows you to test a set of wait conditions, and to conditionally perform any additional actions if the wait can be immediately satisfied, as in the acquisition of a mutex.


### -param WaitBlockArray [in, optional]

If <i>Count</i> &lt;= THREAD_WAIT_OBJECTS, <i>WaitBlockArray</i> can be <b>NULL</b>. Otherwise, this parameter must point to a memory buffer of <code>sizeof(KWAIT_BLOCK * Count)</code> bytes. The routine uses this buffer for record-keeping while performing the wait operation.


### -param Irp [in, optional]

A pointer to the original IRP that corresponds to the I/O operation that was issued by the user and that can be canceled by the user.  The caller must ensure that the IRP will remain valid for the duration of this routine and that the IRP must not have a cancel routine set (for example, <a href="kernel.iosetcancelroutine">IoSetCancelRoutine</a> must not have been called on the IRP).  Note that the IRP must be held by the caller, it cannot be passed to a lower-level driver.


## -returns
<b>FsRtlCancellableWaitForMultipleObjects</b> can return one of the following values:
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl>The caller specified <b>WaitAll</b> for the <i>WaitType</i> parameter and all dispatcher objects in the <i>ObjectArray</i> array have been set to the signaled state.
<dl>
<dt><b>STATUS_TIMEOUT</b></dt>
</dl>A time-out occurred before the specified set of wait conditions was met. This value can be returned when the specified set of wait conditions cannot be immediately met and <i>Timeout</i> is set to zero.
<dl>
<dt><b>STATUS_WAIT_0 through STATUS_WAIT_63</b></dt>
</dl>The caller specified <b>WaitAny</b> for <i>WaitType</i> and one of the dispatcher objects in the <i>ObjectArray</i> array has been set to the signaled state.  The lower six bits of the return value encode the zero-based index of the object that satisfied the wait.
<dl>
<dt><b>STATUS_ABANDONED_WAIT_0 through STATUS_ABANDONED_WAIT_63</b></dt>
</dl>The caller attempted to wait for a mutex that has been abandoned.  The lower six bits of the return value encode the zero-based index of the mutex in the <i>ObjectArray</i> array.
<dl>
<dt><b>STATUS_CANCELLED</b></dt>
</dl>The wait was interrupted by a pending cancel request on the specified IRP.  Note that this value is returned only if a valid IRP is passed to <b>FsRtlCancellableWaitForMultipleObjects</b> and the IRP was canceled by <a href="http://go.microsoft.com/fwlink/p/?linkid=64526">CancelSynchronousIo</a>.
<dl>
<dt><b>STATUS_THREAD_IS_TERMINATING</b></dt>
</dl>The wait was interrupted because the thread has been terminated by an application or the user.

 

The return value only indicates the status of the wait. If applicable, the actual status of the I/O request should be obtained directly from another IRP generated in the process of handling the original user-mode IRP.

Note that the NT_SUCCESS macro returns <b>FALSE</b> ("failure") for the STATUS_CANCELLED and STATUS_THREAD_IS_TERMINATING status values and <b>TRUE</b> ("success") for all other status values.


## -remarks
The <b>FsRtlCancellableWaitForMultipleObjects</b> routine executes a cancelable wait operation on dispatcher objects.  If the thread is terminated by the user or by the application, or if <a href="http://go.microsoft.com/fwlink/p/?linkid=64526">CancelSynchronousIo</a> posts a cancel request on a threaded IRP (synchronous IRP) associated with the thread, the wait is canceled.

The <b>FsRtlCancellableWaitForMultipleObjects</b> routine was designed  for support of the <a href="http://go.microsoft.com/fwlink/p/?linkid=51436">I/O Completion/Cancellation Guidelines</a> starting with Windows Vista. The goal of these guidelines is to allow users (or applications) to quickly terminate applications.  This, in turn, requires that applications have the ability to quickly terminate threads that are executing I/O as well as any current I/O operations. This routine provides a way for user threads to block (that is, wait) in the kernel for I/O completion, dispatcher objects, or synchronization variables in a way that allows the wait to be readily canceled. This routine also permits the thread's wait to be terminated if the thread is terminated by a user or an application.

For example, a redirector may need to create one or more secondary IRPs in order to process a user-mode IRP and synchronously wait for the secondary IRPs to complete. One way to do this is to set up an event that will be signaled by the completion routine of the secondary IRP and then wait for the event to be signaled. Then, to perform a cancelable wait operation, <b>FsRtlCancellableWaitForMultipleObjects</b> is called passing in the event associated with the secondary IRP, as well as the original user-mode IRP.  The thread's wait for the event to be signaled is canceled if a pending termination event occurs or if the original user-mode IRP is canceled.

Note that terminating the wait does not automatically cancel any I/O operation that is issued by the caller - that must be handled separately by the caller.

Each thread object has a built-in array of wait blocks that can be used to wait on several objects concurrently. Whenever possible, the built-in array of wait blocks should be used in a wait-multiple operation because no additional wait block storage needs to be allocated and later deallocated. However, if the number of objects that must be waited on concurrently is greater than the number of built-in wait blocks, use the <i>WaitBlockArray</i> parameter to specify an alternate set of wait blocks to be used in the wait operation. Drivers only need to allocate a sufficiently-large memory buffer for <i>WaitBlockArray</i>. The buffer does not need to be initialized, and the drivers can treat it as an opaque structure. The buffer can be freed once the routine returns.

If either <i>Count</i> is greater than MAXIMUM_WAIT_OBJECTS or if <i>WaitBlockArray</i> is <b>NULL</b> and Count is greater than THREAD_WAIT_OBJECTS, the system issues <a href="https://msdn.microsoft.com/library/windows/hardware/ff560236">Bug Check 0xC: MAXIMUM_WAIT_OBJECTS_EXCEEDED</a>.

A special consideration applies when the <i>ObjectArray</i> parameter passed to <b>FsRtlCancellableWaitForMultipleObjects</b> is a mutex. If the dispatcher object that is waited on is a mutex, APC delivery is the same as for all other dispatcher objects during the wait. However, once <b>FsRtlCancellableWaitForMultipleObjects</b> returns with STATUS_SUCCESS and the thread actually holds the mutex, only special kernel-mode APCs are delivered. Delivery of all other APCs, both kernel-mode and user-mode, is disabled. This restriction on the delivery of APCs persists until the mutex is released.

A mutex can be recursively acquired only MINLONG times.  If this limit is exceeded, the routine raises a STATUS_MUTANT_LIMIT_EXCEEDED exception.

<b>FsRtlCancellableWaitForMultipleObjects</b> must be called at IRQL PASSIVE_LEVEL if the optional <i>Irp</i> parameter points to a valid IRP. If the <i>Irp</i> parameter is not used, the routine can be called at IRQL less or equal to APC_LEVEL. Normal kernel APCs can be disabled by the caller, if needed, by calling the <a href="kernel.keentercriticalregion">KeEnterCriticalRegion</a> or <a href="ifsk.fsrtlenterfilesystem">FsRtlEnterFileSystem</a> routines. However, special kernel APCs must not be disabled. 

<b>FsRtlCancellableWaitForMultipleObjects</b> will assert on debug builds if the IRQL is greater or equal to APC_LEVEL and the <i>Irp</i> parameter points to a valid IRP.


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
This routine is available starting with Windows Vista.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
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
See Remarks section.

</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="ifsk.fsrtlcancellablewaitforsingleobject">FsRtlCancellableWaitForSingleObject</a>
</dt>
<dt>
<a href="kernel.exinitializefastmutex">ExInitializeFastMutex</a>
</dt>
<dt>
<a href="kernel.keinitializeevent">KeInitializeEvent</a>
</dt>
<dt>
<a href="kernel.keinitializemutex">KeInitializeMutex</a>
</dt>
<dt>
<a href="kernel.keinitializesemaphore">KeInitializeSemaphore</a>
</dt>
<dt>
<a href="kernel.keinitializetimer">KeInitializeTimer</a>
</dt>
<dt>
<a href="kernel.kewaitformultipleobjects">KeWaitForMultipleObjects</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553344">KeWaitForMutexObject</a>
</dt>
<dt>
<a href="kernel.kewaitforsingleobject">KeWaitForSingleObject</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FsRtlCancellableWaitForMultipleObjects routine%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
