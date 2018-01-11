---
UID: NS.WWAN._WWAN_SMS_SEND_PDU
title: _WWAN_SMS_SEND_PDU
author: windows-driver-content
description: The WWAN_SMS_SEND_PDU structure represents a PDU-style SMS message.
old-location: netvista\wwan_sms_send_pdu.htm
old-project: NetVista
ms.assetid: 94d19d5b-8fa5-437d-9359-e35ef103f380
ms.author: windowsdriverdev
ms.date: 12/14/2017
ms.keywords: _WWAN_SMS_SEND_PDU, PWWAN_SMS_SEND_PDU, WWAN_SMS_SEND_PDU, *PWWAN_SMS_SEND_PDU
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_SMS_SEND_PDU
req.alt-loc: wwan.h
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
req.product: Windows 10 or later.
---

# _WWAN_SMS_SEND_PDU structure



## -description
The WWAN_SMS_SEND_PDU structure represents a PDU-style SMS message.



## -syntax

````
typedef struct _WWAN_SMS_SEND_PDU {
  BYTE Size;
  CHAR PduData[WWAN_SMS_PDU_HEX_BUF_LEN];
} WWAN_SMS_SEND_PDU, *PWWAN_SMS_SEND_PDU;
````


## -struct-fields

### -field Size

For GSM-based devices that support PDU-style SMS messages, the size, in bytes, of the message
     before conversion to hexadecimal.
     

For CDMA-based devices that support sending SMS messages in binary format, the size, in bytes, of the
     message in 
     <b>PduData</b> .

The following table lists the different values for the 
     <b>SmsFormat</b> member of the 
     <a href="netvista.wwan_sms_send">WWAN_SMS_SEND</a> structure and their
     corresponding range that is allowed in this member.

<table>
<tr>
<th>SmsFormat</th>
<th>Size</th>
</tr>
<tr>
<td>
WwanSmsFormatPdu

</td>
<td>
1 to WWAN_SMS_RAW_PDU_LEN

</td>
</tr>
<tr>
<td>
WwanSmsFormatCdma

</td>
<td>
1 to WWAN_SMS_CDMA_MAX_MSG_LEN

</td>
</tr>
</table>
 

<div class="alert"><b>Note</b>  For GSM-based devices, if 
     <b>ElementType</b> is set to 
     <b>WwanStructSmsPdu</b>, this member describes the size, in bytes, of 
     <b>PduData</b> excluding the Service Center address. The first byte of 
     <b>PduData</b> represents the size of the Service Center address that the miniport driver must add when
     it calculates the exact size of the 
     <b>PduData</b> buffer.
     <p class="note">For example:

<p class="note">If 
     <b>PduData</b> [0] = 0, then the size of 
     <b>PduData</b> is 
     <b>Size</b> + 1.

<p class="note">If 
     <b>PduData</b> [0] != 0, then the size of 
     <b>PduData</b> is 
     <b>Size</b> + 
     <b>PduData</b> [0].

</div>
<div> </div>

### -field PduData

A NULL-terminated string that represents the content of the record.
     

For GSM-based devices, the contents are coded in a hexadecimal string format (according to the 3GPP
     TS 27.005 and 3GPP TS 23.040 standards) that represents the SMS text message.

For CDMA-based devices that support sending SMS messages in binary format (that is, miniport drivers
     that return WWAN_SMS_CAPS_PDU_SEND in the 
     <b>WwanSmsCaps</b> member of 
     <a href="netvista.wwan_device_caps">WWAN_DEVICE_CAPS</a>), 
     <b>PduData</b> contains the SMS message as a byte array, as defined in section 3.4.2.1 SMS Point-to-Point
     Message in the 3GPP2 specification C.S0015-A "Short Message Service (SMS) for Wideband Spread Spectrum
     Systems". SMS will only support Wireless Messaging Teleservice (WMT) format. Miniport drivers should
     typecast this information to BYTE[] for CDMA-based devices. It is not coded in hexadecimal string
     format.


## -remarks


## -requirements
<table>
<tr>
<th width="30%">
Version

</th>
<td width="70%">
Available in Windows 7 and later versions of Windows.

</td>
</tr>
<tr>
<th width="30%">
Header

</th>
<td width="70%">
<dl>
<dt>Wwan.h (include Wwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="netvista.wwan_sms_send">WWAN_SMS_SEND</a>
</dt>
</dl>
 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [NetVista\netvista]:%20WWAN_SMS_SEND_PDU structure%20 RELEASE:%20(12/14/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
