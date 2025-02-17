---
title: DIF_NEWDEVICEWIZARD_PREANALYZE
description: DIF_NEWDEVICEWIZARD_PREANALYZE
keywords: ["DIF_NEWDEVICEWIZARD_PREANALYZE Device and Driver Installation"]
topic_type:
- apiref
api_name:
- DIF_NEWDEVICEWIZARD_PREANALYZE
api_location:
- Setupapi.h
api_type:
- HeaderDef
ms.date: 10/17/2018
---

# DIF_NEWDEVICEWIZARD_PREANALYZE


A DIF_NEWDEVICEWIZARD_PREANALYZE request allows an installer to supply wizard pages that Windows displays to the user before it displays the analyze page. This request is only used during manual installation of non-PnP devices.

### When Sent

After the user has selected a driver, but before Windows registers the device that makes the device node (*devnode*) "live."

### Who Handles

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Class Co-installer</p></td>
<td align="left"><p>Can handle</p></td>
</tr>
<tr class="even">
<td align="left"><p>Device Co-installer</p></td>
<td align="left"><p>Does not handle</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Class Installer</p></td>
<td align="left"><p>Can handle</p></td>
</tr>
</tbody>
</table>

 

### Installer Input

<a href="" id="deviceinfoset"></a>*DeviceInfoSet*  
Supplies a handle to the [device information set](./device-information-sets.md) that contains the device.

<a href="" id="deviceinfodata"></a>*DeviceInfoData*  
Supplies a pointer to an [**SP_DEVINFO_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_devinfo_data) structure that identifies the device in the device information set.

<a href="" id="device-installation-parameters-"></a>Device Installation Parameters   
There are device installation parameters ([**SP_DEVINSTALL_PARAMS**](/windows/win32/api/setupapi/ns-setupapi-sp_devinstall_params_a)) associated with the *DeviceInfoData*.

<a href="" id="class-installation-parameters"></a>Class Installation Parameters  
An [**SP_NEWDEVICEWIZARD_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_newdevicewizard_data) structure is associated with the *DeviceInfoData*.

### Installer Output

<a href="" id="device-installation-parameters"></a>Device Installation Parameters  
An installer can modify the flags in the device installation parameters. Windows does not check the flags upon completion of this DIF request. However, it checks them later in the installation process.

<a href="" id="class-installation-parameters"></a>Class Installation Parameters  
An installer can modify the [**SP_NEWDEVICEWIZARD_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_newdevicewizard_data) to supply custom wizard page(s).

### Installer Return Value

If a co-installer does not handle this DIF request it returns NO_ERROR from its preprocessing pass. If a co-installer handles this request it can return NO_ERROR, ERROR_DI_POSTPROCESSING_REQUIRED, or a Win32 error code.

A class installer returns NO_ERROR if it successfully supplies page(s). Otherwise, a class installer returns ERROR_DI_DO_DEFAULT or a Win32 error code.

### Default DIF Code Handler

None

### Installer Operation

A DIF_NEWDEVICEWIZARD_PREANALYZE request allows an installer to supply wizard pages that Windows displays to the user before it displays the analyze page. These pages can be thought of as "postselect" pages. This request is only used during manual installation of non-PnP devices.

An installer might use a custom preanalyze page, for example, to choose a COM port after a modem device is selected.

If an installer adds custom preselect page(s), the installer should first check whether **NumDynamicPages** in the class install parameters has reached MAX_INSTALLWIZARD_DYNAPAGES.

An installer should supply a Wizard 97 header title and a header subtitle in the PROPSHEETPAGE structure for a custom wizard page. An installer should not replace the system-supplied wizard title. See the Microsoft Windows SDK for documentation of the PROPSHEETPAGE structure and for more information about property pages.

For more information about DIF codes, see [Handling DIF Codes](./handling-dif-codes.md).

## Requirements

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>Supported in Microsoft Windows 2000 and later versions of Windows.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Header</p></td>
<td align="left">Setupapi.h (include Setupapi.h)</td>
</tr>
</tbody>
</table>

## See also


[**DIF_NEWDEVICEWIZARD_PRESELECT**](dif-newdevicewizard-preselect.md)

[**DIF_NEWDEVICEWIZARD_POSTANALYZE**](dif-newdevicewizard-postanalyze.md)

[**DIF_NEWDEVICEWIZARD_SELECT**](dif-newdevicewizard-select.md)

[**SP_DEVINFO_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_devinfo_data)

[**SP_DEVINSTALL_PARAMS**](/windows/win32/api/setupapi/ns-setupapi-sp_devinstall_params_a)

[**SP_NEWDEVICEWIZARD_DATA**](/windows/win32/api/setupapi/ns-setupapi-sp_newdevicewizard_data)

 

