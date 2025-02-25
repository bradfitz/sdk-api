---
UID: NF:ntsecapi.LsaLookupSids2
title: LsaLookupSids2 function (ntsecapi.h)
description: Looks up the names that correspond to an array of security identifiers (SIDs) and supports Internet provider identities. If LsaLookupSids2 cannot find a name that corresponds to a SID, the function returns the SID in character form.
helpviewer_keywords: ["LSA_LOOKUP_DISALLOW_CONNECTED_ACCOUNT_INTERNET_SID","LSA_LOOKUP_PREFER_INTERNET_NAMES","LSA_LOOKUP_RETURN_LOCAL_NAMES","LsaLookupSids2","LsaLookupSids2 function [Security]","ntsecapi/LsaLookupSids2","security.lsalookupsids2"]
old-location: security\lsalookupsids2.htm
tech.root: security
ms.assetid: 6B30D1FF-35DC-44E8-A765-36A5761EC0CE
ms.date: 12/05/2018
ms.keywords: LSA_LOOKUP_DISALLOW_CONNECTED_ACCOUNT_INTERNET_SID, LSA_LOOKUP_PREFER_INTERNET_NAMES, LSA_LOOKUP_RETURN_LOCAL_NAMES, LsaLookupSids2, LsaLookupSids2 function [Security], ntsecapi/LsaLookupSids2, security.lsalookupsids2
req.header: ntsecapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8 [desktop apps only]
req.target-min-winversvr: Windows Server 2012 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Advapi32.lib
req.dll: Advapi32.dll
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - LsaLookupSids2
 - ntsecapi/LsaLookupSids2
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - Advapi32.dll
 - API-MS-Win-Security-lsapolicy-l1-1-0.dll
 - sechost.dll
 - API-MS-Win-Security-LSAPolicy-L1-1-1.dll
api_name:
 - LsaLookupSids2
---

# LsaLookupSids2 function


## -description

The <b>LsaLookupSids2</b> function looks up the names that correspond to an array of <a href="https://docs.microsoft.com/windows/desktop/SecGloss/s-gly">security identifiers</a> (SIDs) and supports Internet provider identities. If <b>LsaLookupSids2</b> cannot find a name that corresponds to a SID, the function returns the SID in character form. You should use this function instead of the <a href="https://docs.microsoft.com/windows/desktop/api/ntsecapi/nf-ntsecapi-lsalookupsids">LsaLookupSids</a> function.

## -parameters

### -param PolicyHandle [in]

A handle to a <a href="https://docs.microsoft.com/windows/desktop/SecMgmt/policy-object">Policy</a> object. This handle must have the POLICY_LOOKUP_NAMES access right. For more information, see 
<a href="https://docs.microsoft.com/windows/desktop/SecMgmt/opening-a-policy-object-handle">Opening a Policy Object Handle</a>.

### -param LookupOptions [in]

Flags that modify the lookup behavior. 

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%"><a id="LSA_LOOKUP_DISALLOW_CONNECTED_ACCOUNT_INTERNET_SID"></a><a id="lsa_lookup_disallow_connected_account_internet_sid"></a><dl>
<dt><b>LSA_LOOKUP_DISALLOW_CONNECTED_ACCOUNT_INTERNET_SID</b></dt>
</dl>
</td>
<td width="60%">
Internet SIDs from identity providers for connected accounts are disallowed. Connected accounts are those accounts which have a corresponding shadow account in the local SAM database connected to an online identity provider.  For example, MicrosoftAccount is a connected account.

</td>
</tr>
<tr>
<td width="40%"><a id="LSA_LOOKUP_PREFER_INTERNET_NAMES"></a><a id="lsa_lookup_prefer_internet_names"></a><dl>
<dt><b>LSA_LOOKUP_PREFER_INTERNET_NAMES</b></dt>
</dl>
</td>
<td width="60%">
 Returns the internet names. Otherwise the NT4 style name (domain\username) is returned. The exception is if the Microsoft Account internet SID is specified, in which case the internet name is returned unless <b>LSA_LOOKUP_DISALLOW_NON_WINDOWS_INTERNET_SID</b>  is specified.

</td>
</tr>
<tr>
<td width="40%"><a id="LSA_LOOKUP_RETURN_LOCAL_NAMES"></a><a id="lsa_lookup_return_local_names"></a><dl>
<dt><b>LSA_LOOKUP_RETURN_LOCAL_NAMES</b></dt>
</dl>
</td>
<td width="60%">
Always returns local SAM account names even for Internet provider identities.

</td>
</tr>
</table>

### -param Count [in]

Specifies the number of SIDs in the <i>Sids</i> array. This is also the number of entries returned in the <i>Names</i> array. This value must be less than or equal to 20480.

### -param Sids [in]

Pointer to an array of SID pointers to look up. The SIDs can be well-known SIDs, user, group, or local group account SIDs, or domain SIDs.

### -param ReferencedDomains [out]

Receives a pointer to a pointer to a <a href="https://docs.microsoft.com/windows/desktop/api/lsalookup/ns-lsalookup-lsa_referenced_domain_list">LSA_REFERENCED_DOMAIN_LIST</a> structure. The <b>Domains</b> member of this structure is an array that contains an entry for each domain in which a SID was found. The entry for each domain contains the SID and flat name of the domain. For Windows domains, the flat name is the NetBIOS name. For links with non–Windows domains, the flat name is the identifying name of that domain, or it is <b>NULL</b>. 




When you no longer need the information, pass the returned pointer to 
<a href="https://docs.microsoft.com/windows/desktop/api/ntsecapi/nf-ntsecapi-lsafreememory">LsaFreeMemory</a>. This memory must be freed even when the function fails with the either of the error codes <b>STATUS_NONE_MAPPED</b> or <b>STATUS_SOME_NOT_MAPPED</b>

### -param Names [out]

Receives a pointer to an array of 
<a href="https://docs.microsoft.com/windows/desktop/api/lsalookup/ns-lsalookup-lsa_translated_name">LSA_TRANSLATED_NAME</a> structures. Each entry in the <i>Names</i> array contains the name information for the corresponding entry in the <i>Sids</i> array. For account SIDs, the <b>Name</b> member of each structure contains the isolated name of the account. For domain SIDs, the <b>Name</b> member is not valid. 




The <b>DomainIndex</b> member of each entry in the <i>Names</i> array is the index of an entry in the <b>Domains</b> array returned in the <i>ReferencedDomains</i> parameter. The index identifies the <b>Domains</b> array for the domain in which the SID was found.

When you no longer need the information, pass the returned pointer to 
<a href="https://docs.microsoft.com/windows/desktop/api/ntsecapi/nf-ntsecapi-lsafreememory">LsaFreeMemory</a>. This memory must be freed even when the function fails with the either of the error codes <b>STATUS_NONE_MAPPED</b> or <b>STATUS_SOME_NOT_MAPPED</b>

## -returns

If the function succeeds, the return value is one of the following <b>NTSTATUS</b> values.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_SOME_NOT_MAPPED</b></dt>
</dl>
</td>
<td width="60%">
Some of the SIDs could not be translated. This is an informational-level return value.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl>
</td>
<td width="60%">
All of the SIDs were found and successfully translated.

</td>
</tr>
</table>
 

If the function fails, the return value is an <b>NTSTATUS</b> code, which can be one of the following values or one of the 
<a href="https://docs.microsoft.com/windows/desktop/SecMgmt/management-return-values">LSA Policy Function Return Values</a>.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_NONE_MAPPED</b></dt>
</dl>
</td>
<td width="60%">
None of the SIDs were translated. This is an error-level return value.

</td>
</tr>

<tr>
<td width="40%">
<dl>
<dt><b>STATUS_TOO_MANY_SIDS</b></dt>
<dt></dt>
</dl>
</td>
<td width="60%">
The Sids array parameter was too large.
</td>
</tr>
</table>
 

You can use the 
<a href="https://docs.microsoft.com/windows/desktop/api/ntsecapi/nf-ntsecapi-lsantstatustowinerror">LsaNtStatusToWinError</a> function to convert the <b>NTSTATUS</b> code to a Windows error code.

## -remarks

The flag LSA_LOOKUP_PREFER_INTERNET_NAMES  should be used for internet accounts such as MicrosoftAccount and Azure Active Directory accounts.
When this flag is specified then SID-Name lookup returns the UPN of the account in the form MicrosoftAccount\foo@outlook.com or AzureAD\foo@contoso.com. 
For Microsoft Accounts both the local SAM SID and the internet SID result in the UPN being returned if this flag is specified.
If LSA_LOOKUP_PREFER_INTERNET_NAMES is not specified then for AAD accounts the NT4 style name of the form AzureAD\foo is returned. The NT4 style name is machine specific and its usage should be carefully evaluated and if possible should be avoided.
For MicrosoftAccounts if LSA_LOOKUP_PREFER_INTERNET_NAMES is not specified then the local SID of the account translates to the local SAM name, and the internet SID translates to the UPN name.

For account SIDs, the string returned in the <b>Name</b> member is the isolated name of the account (for example, user_name). If you need the composite name of the account (for example, Acctg\user_name), get the domain name from the <i>ReferencedDomains</i> buffer and append a backslash and the isolated name.

If the <b>LsaLookupSids2</b> function cannot translate a SID, the function uses the following algorithm:

<ol>
<li>If the SID's domain is known, the <i>ReferencedDomains</i> buffer contains an entry for the domain, and the string returned in the <i>Names</i> parameter is a <a href="https://docs.microsoft.com/windows/desktop/SecGloss/u-gly">Unicode</a> representation of the account's relative identifier (RID) from the SID.</li>
<li>If the SID's domain is not known, the string returned in the <i>Names</i> parameter is a Unicode representation of the entire SID, and there is no domain record for this SID in the <i>ReferencedDomains</i> buffer.</li>
</ol>
In addition to looking up SIDs for local accounts, local domain accounts, and explicitly trusted domain accounts, <b>LsaLookupSids2</b> can look up SIDs for any account in any domain in the Windows forest, including SIDs that appear only in the <b>SIDhistory</b> field of an account in the forest. The <b>SIDhistory</b> field stores the former SIDs of an account that has been moved from another domain. To perform these searches, the function queries the global catalog of the forest.

## -see-also

<a href="https://docs.microsoft.com/windows/desktop/api/lsalookup/ns-lsalookup-lsa_referenced_domain_list">LSA_REFERENCED_DOMAIN_LIST</a>



<a href="https://docs.microsoft.com/windows/desktop/api/lsalookup/ns-lsalookup-lsa_translated_name">LSA_TRANSLATED_NAME</a>



<a href="https://docs.microsoft.com/windows/desktop/api/ntsecapi/nf-ntsecapi-lsaopenpolicy">LsaOpenPolicy</a>

