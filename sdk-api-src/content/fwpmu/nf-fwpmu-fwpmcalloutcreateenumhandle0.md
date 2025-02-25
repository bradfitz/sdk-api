---
UID: NF:fwpmu.FwpmCalloutCreateEnumHandle0
title: FwpmCalloutCreateEnumHandle0 function (fwpmu.h)
description: Creates a handle used to enumerate a set of callout objects.
helpviewer_keywords: ["FwpmCalloutCreateEnumHandle0","FwpmCalloutCreateEnumHandle0 function [Filtering]","fwp.fwpmcalloutcreateenumhandle0_func","fwpmu/FwpmCalloutCreateEnumHandle0"]
old-location: fwp\fwpmcalloutcreateenumhandle0_func.htm
tech.root: fwp
ms.assetid: bd37eebb-8a07-4b67-9595-34cc96463254
ms.date: 12/05/2018
ms.keywords: FwpmCalloutCreateEnumHandle0, FwpmCalloutCreateEnumHandle0 function [Filtering], fwp.fwpmcalloutcreateenumhandle0_func, fwpmu/FwpmCalloutCreateEnumHandle0
req.header: fwpmu.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows Vista [desktop apps only]
req.target-min-winversvr: Windows Server 2008 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fwpuclnt.lib
req.dll: Fwpuclnt.dll
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - FwpmCalloutCreateEnumHandle0
 - fwpmu/FwpmCalloutCreateEnumHandle0
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - Fwpuclnt.dll
api_name:
 - FwpmCalloutCreateEnumHandle0
---

# FwpmCalloutCreateEnumHandle0 function


## -description

The <b>FwpmCalloutCreateEnumHandle0</b> function  creates a handle used to enumerate a set of callout objects.

## -parameters

### -param engineHandle [in]

Type: <b>HANDLE</b>

Handle for an open session to the filter engine. Call <a href="https://docs.microsoft.com/windows/desktop/api/fwpmu/nf-fwpmu-fwpmengineopen0">FwpmEngineOpen0</a> to open a session to the filter engine.

### -param enumTemplate [in, optional]

Type: [FWPM_CALLOUT_ENUM_TEMPLATE0](https://docs.microsoft.com/windows/desktop/api/fwpmtypes/ns-fwpmtypes-fwpm_callout_enum_template0)*</b>

Template to selectively restrict the enumeration.

### -param enumHandle [out]

Type: <b>HANDLE*</b>

Handle of the newly created enumeration.

## -returns

Type: <b>DWORD</b>

<table>
<tr>
<th>Return code/value</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_SUCCESS</b></dt>
<dt>0</dt>
</dl>
</td>
<td width="60%">
The enumerator was created successfully.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>FWP_E_* error code</b></dt>
<dt>0x80320001—0x80320039</dt>
</dl>
</td>
<td width="60%">
A Windows Filtering Platform (WFP) specific error. See <a href="https://docs.microsoft.com/windows/desktop/FWP/wfp-error-codes">WFP Error Codes</a> for details.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>RPC_* error code</b></dt>
<dt>0x80010001—0x80010122</dt>
</dl>
</td>
<td width="60%">
Failure to communicate with the remote or local firewall engine.

</td>
</tr>
</table>

## -remarks

If <i>enumTemplate</i> is <b>NULL</b>, all callout objects are returned.

The enumerator is not "live", meaning it does not reflect changes made to the system after the call to <b>FwpmCalloutCreateEnumHandle0</b> returns. If you need to ensure that the results are current, you must call <b>FwpmCalloutCreateEnumHandle0</b> and <a href="https://docs.microsoft.com/windows/desktop/api/fwpmu/nf-fwpmu-fwpmcalloutenum0">FwpmCalloutEnum0</a> from within the same explicit transaction.

The caller must call <a href="https://docs.microsoft.com/windows/desktop/api/fwpmu/nf-fwpmu-fwpmcalloutdestroyenumhandle0">FwpmCalloutDestroyEnumHandle0</a> to free the returned handle.

The caller needs <a href="https://docs.microsoft.com/windows/desktop/FWP/access-right-identifiers">FWPM_ACTRL_ENUM</a> access to the callouts' containers and <b>FWPM_ACTRL_READ</b> access to the callouts. Only callouts to which the caller has <b>FWPM_ACTRL_READ</b> access will be returned. See <a href="https://docs.microsoft.com/windows/desktop/FWP/access-control">Access Control</a> for more information.

<b>FwpmCalloutCreateEnumHandle0</b> is a specific implementation of FwpmCalloutCreateEnumHandle. See <a href="https://docs.microsoft.com/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows">WFP Version-Independent Names and Targeting Specific Versions of Windows</a>  for more information.

## -see-also

[FWPM_CALLOUT_ENUM_TEMPLATE0](https://docs.microsoft.com/windows/desktop/api/fwpmtypes/ns-fwpmtypes-fwpm_callout_enum_template0)

