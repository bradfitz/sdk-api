---
UID: NF:docobj.IOleCommandTarget.QueryStatus
title: IOleCommandTarget::QueryStatus (docobj.h)
description: Queries the object for the status of one or more commands generated by user interface events.
helpviewer_keywords: ["IOleCommandTarget interface [COM]","QueryStatus method","IOleCommandTarget.QueryStatus","IOleCommandTarget::QueryStatus","QueryStatus","QueryStatus method [COM]","QueryStatus method [COM]","IOleCommandTarget interface","_ole_iolecommandtarget_querystatus","com.iolecommandtarget_querystatus","docobj/IOleCommandTarget::QueryStatus"]
old-location: com\iolecommandtarget_querystatus.htm
tech.root: com
ms.assetid: 8acbf788-f113-43d9-800d-aad84db24498
ms.date: 12/05/2018
ms.keywords: IOleCommandTarget interface [COM],QueryStatus method, IOleCommandTarget.QueryStatus, IOleCommandTarget::QueryStatus, QueryStatus, QueryStatus method [COM], QueryStatus method [COM],IOleCommandTarget interface, _ole_iolecommandtarget_querystatus, com.iolecommandtarget_querystatus, docobj/IOleCommandTarget::QueryStatus
req.header: docobj.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 2000 Professional [desktop apps only]
req.target-min-winversvr: Windows 2000 Server [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: DocObj.Idl
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - IOleCommandTarget::QueryStatus
 - docobj/IOleCommandTarget::QueryStatus
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - DocObj.h
api_name:
 - IOleCommandTarget.QueryStatus
---

# IOleCommandTarget::QueryStatus


## -description

Queries the object for the status of one or more commands generated by user interface events.

## -parameters

### -param pguidCmdGroup [in]

The unique identifier of the command group; can be <b>NULL</b> to specify the standard group. All the commands that are passed in the <i>prgCmds</i> array must belong to the group specified by <i>pguidCmdGroup</i>.

### -param cCmds [in]

The number of commands in the <i>prgCmds</i> array.

### -param prgCmds [in, out]

A caller-allocated array of <a href="https://docs.microsoft.com/windows/desktop/api/docobj/ns-docobj-olecmd">OLECMD</a> structures that indicate the commands for which the caller needs status information. This method fills the <b>cmdf</b> member of each structure with values taken from the <a href="https://docs.microsoft.com/windows/desktop/api/docobj/ne-docobj-olecmdf">OLECMDF</a> enumeration.

### -param pCmdText [in, out]

A pointer to an <a href="https://docs.microsoft.com/windows/desktop/api/docobj/ns-docobj-olecmdtext">OLECMDTEXT</a> structure in which to return name and/or status information of a single command. This parameter can be <b>NULL</b> to indicate that the caller does not need this information.

## -returns

This method returns S_OK on success. Other possible return values include the following.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>E_FAIL</b></dt>
</dl>
</td>
<td width="60%">
The operation failed.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>E_UNEXPECTED</b></dt>
</dl>
</td>
<td width="60%">
An unexpected error has occurred.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>E_POINTER</b></dt>
</dl>
</td>
<td width="60%">
The <i>prgCmds</i> argument is <b>NULL</b>.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>OLECMDERR_E_UNKNOWNGROUP</b></dt>
</dl>
</td>
<td width="60%">
The <i>pguidCmdGroup</i> parameter is not <b>NULL</b> but does not specify a recognized command group.

</td>
</tr>
</table>

## -remarks

Callers use <b>QueryStatus</b> to determine which commands are supported by a target object. The caller can then disable unavailable commands that would otherwise be routed to the object. The caller can also use this method to get the name or status of a single command.

## -see-also

<a href="https://docs.microsoft.com/windows/desktop/api/docobj/nn-docobj-iolecommandtarget">IOleCommandTarget</a>



<a href="https://docs.microsoft.com/windows/desktop/api/docobj/ns-docobj-olecmd">OLECMD</a>



<a href="https://docs.microsoft.com/windows/desktop/api/docobj/ne-docobj-olecmdf">OLECMDF</a>



<a href="https://docs.microsoft.com/windows/desktop/api/docobj/ns-docobj-olecmdtext">OLECMDTEXT</a>

