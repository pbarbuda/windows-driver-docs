---
title: WSK_RELEASE_SD
description: WSK_RELEASE_SD
ms.date: 07/18/2017
keywords:
 - WSK_RELEASE_SD Network Drivers Starting with Windows Vista
---

# WSK\_RELEASE\_SD


A WSK application uses the WSK\_RELEASE\_SD client control operation to release a cached copy of a security descriptor that either was previously obtained by using the [**WSK\_CACHE\_SD**](wsk-cache-sd.md) client control operation or was retrieved by using the [**SO\_WSK\_SECURITY**](so-wsk-security.md) socket option.

To release a cached copy of a security descriptor, a WSK application calls the [**WskControlClient**](/windows-hardware/drivers/ddi/wsk/nc-wsk-pfn_wsk_control_client) function with the following parameters.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ControlCode</em></p></td>
<td><p>WSK_RELEASE_SD</p></td>
</tr>
<tr class="even">
<td><p><em>InputSize</em></p></td>
<td><p>sizeof(PSECURITY_DESCRIPTOR)</p></td>
</tr>
<tr class="odd">
<td><p><em>InputBuffer</em></p></td>
<td><p>A pointer to a PSECURITY_DESCRIPTOR-typed variable. This variable contains a pointer to the SECURITY_DESCRIPTOR structure that defines the cached security descriptor that is being released.</p></td>
</tr>
<tr class="even">
<td><p><em>OutputSize</em></p></td>
<td><p>0</p></td>
</tr>
<tr class="odd">
<td><p><em>OutputBuffer</em></p></td>
<td><p><strong>NULL</strong></p></td>
</tr>
<tr class="even">
<td><p><em>OutputSizeReturned</em></p></td>
<td><p><strong>NULL</strong></p></td>
</tr>
<tr class="odd">
<td><p><em>Irp</em></p></td>
<td><p><strong>NULL</strong></p></td>
</tr>
</tbody>
</table>

See the reference page for the [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) structure for more information.

The *Irp* parameter must be **NULL** for this client control operation.

## Requirements

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Available in Windows Vista and later versions of the Windows operating systems.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Wsk.h (include Wsk.h)</td>
</tr>
</tbody>
</table>

 

