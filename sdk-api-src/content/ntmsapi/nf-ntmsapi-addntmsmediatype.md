---
UID: NF:ntmsapi.AddNtmsMediaType
title: AddNtmsMediaType function (ntmsapi.h)
description: The AddNtmsMediaType function adds the specified media type to the specified library if there is not currently a relation in the library object. The function then creates the system media pools if they do not exist.
helpviewer_keywords: ["AddNtmsMediaType","AddNtmsMediaType function [Files]","_zaw_addntmsmediatype","base.addntmsmediatype","fs.addntmsmediatype","ntmsapi/AddNtmsMediaType"]
old-location: fs\addntmsmediatype.htm
tech.root: fs
ms.assetid: fa8ad4af-eeb8-445e-ac6c-671badb651ec
ms.date: 12/05/2018
ms.keywords: AddNtmsMediaType, AddNtmsMediaType function [Files], _zaw_addntmsmediatype, base.addntmsmediatype, fs.addntmsmediatype, ntmsapi/AddNtmsMediaType
req.header: ntmsapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows XP [desktop apps only]
req.target-min-winversvr: Windows Server 2003 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ntmsapi.lib
req.dll: Ntmsapi.dll
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - AddNtmsMediaType
 - ntmsapi/AddNtmsMediaType
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - Ntmsapi.dll
api_name:
 - AddNtmsMediaType
---

# AddNtmsMediaType function


## -description

<p class="CCE_Message">[<a href="https://docs.microsoft.com/previous-versions/windows/desktop/bb540725(v=vs.85)">Removable Storage Manager</a> is no longer available as of Windows 7 and  Windows Server 2008 R2.]

The 
<b>AddNtmsMediaType</b> function adds the specified media type to the specified library if there is not currently a relation in the library object. The function then creates the system 
<a href="https://docs.microsoft.com/previous-versions/windows/desktop/bb540696(v=vs.85)">media pools</a> if they do not exist.

## -parameters

### -param hSession [in]

Handle to the session returned by the 
<a href="https://docs.microsoft.com/windows/desktop/api/ntmsapi/nf-ntmsapi-openntmssessiona">OpenNtmsSession</a> function.

### -param lpMediaTypeId [in]

Unique identifier of the media type to add to the library.

### -param lpLibId [in]

Unique identifier of the library to which the media type will be added.

## -returns

This function returns one of the following values.

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_ACCESS_DENIED</b></dt>
</dl>
</td>
<td width="60%">
NTMS_MODIFY_ACCESS to the library is denied. Other security errors are possible, but they would indicate a security subsystem error.

<b>Windows XP:  </b>NTMS_CONTROL_ACCESS to the library is denied. Other security errors are possible, but they would indicate a security subsystem error.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_DATABASE_FAILURE</b></dt>
</dl>
</td>
<td width="60%">
The database is inaccessible or damaged.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_DATABASE_FULL</b></dt>
</dl>
</td>
<td width="60%">
The database is full.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_INVALID_HANDLE</b></dt>
</dl>
</td>
<td width="60%">
The session handle is missing or is not valid.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_INVALID_LIBRARY</b></dt>
</dl>
</td>
<td width="60%">
The library ID is not valid.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_INVALID_MEDIA</b></dt>
</dl>
</td>
<td width="60%">
The media type is not valid.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_INVALID_PARAMETER</b></dt>
</dl>
</td>
<td width="60%">
The media type or library ID is missing.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_NOT_ENOUGH_MEMORY</b></dt>
</dl>
</td>
<td width="60%">
There was an allocation failure during processing.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_SUCCESS</b></dt>
</dl>
</td>
<td width="60%">
The function was successful.

</td>
</tr>
</table>

## -see-also

<a href="https://docs.microsoft.com/windows/desktop/api/ntmsapi/nf-ntmsapi-deletentmsmediatype">DeleteNtmsMediaType</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/rsm/removable-storage-manager-functions">Media Services Functions</a>

