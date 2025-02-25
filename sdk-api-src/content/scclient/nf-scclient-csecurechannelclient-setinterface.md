---
UID: NF:scclient.CSecureChannelClient.SetInterface
title: CSecureChannelClient::SetInterface (scclient.h)
description: The SetInterface method is used by applications to set the IComponentAuthenticate interface to use for Secure Authenticated Channel (SAC) operations.
helpviewer_keywords: ["CSecureChannelClient class [windows Media Device Manager]","SetInterface method","CSecureChannelClient.SetInterface","CSecureChannelClient::SetInterface","CSecureChannelClientSetInterface","SetInterface","SetInterface method [windows Media Device Manager]","SetInterface method [windows Media Device Manager]","CSecureChannelClient class","scclient/CSecureChannelClient::SetInterface","wmdm.csecurechannelclient_setinterface"]
old-location: wmdm\csecurechannelclient_setinterface.htm
tech.root: WMDM
ms.assetid: b1af8f10-7bad-4f85-89f1-b983af6d4dc9
ms.date: 12/05/2018
ms.keywords: CSecureChannelClient class [windows Media Device Manager],SetInterface method, CSecureChannelClient.SetInterface, CSecureChannelClient::SetInterface, CSecureChannelClientSetInterface, SetInterface, SetInterface method [windows Media Device Manager], SetInterface method [windows Media Device Manager],CSecureChannelClient class, scclient/CSecureChannelClient::SetInterface, wmdm.csecurechannelclient_setinterface
req.header: scclient.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Mssachlp.lib
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - CSecureChannelClient::SetInterface
 - scclient/CSecureChannelClient::SetInterface
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - mssachlp.lib
 - mssachlp.dll
api_name:
 - CSecureChannelClient.SetInterface
---

# CSecureChannelClient::SetInterface


## -description

The <b>SetInterface</b> method is used by applications to set the <b>IComponentAuthenticate</b> interface to use for Secure Authenticated Channel (SAC) operations.

## -parameters

### -param pComponentAuth [in]

Pointer to an <a href="https://docs.microsoft.com/windows/desktop/api/mswmdm/nn-mswmdm-icomponentauthenticate">IComponentAuthenticate</a> interface. The caller is responsible for calling <b>Release</b> on the retrieved interface.

## -returns

The method returns an <b>HRESULT</b>. All the interface methods in Windows Media Device Manager can return any of the following classes of error codes:

<ul>
<li>Standard COM error codes </li>
<li>Windows error codes converted to HRESULT values </li>
<li>Windows Media Device Manager error codes </li>
</ul>
For an extensive list of possible error codes, see <a href="https://docs.microsoft.com/windows/desktop/WMDM/error-codes">Error Codes</a>.

Possible values include, but are not limited to, those in the following table.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td>S_OK</td>
<td>The method succeeded.</td>
</tr>
<tr>
<td>E_INVALIDARG</td>
<td>The pComponentAuth parameter is invalid or is a <b>NULL</b> pointer.</td>
</tr>
<tr>
<td>E_FAIL</td>
<td>An unspecified error occurred.</td>
</tr>
</table>

## -remarks

The SAC interface is the <b>IComponentAuthenticate</b> interface. Applications use the <b>IComponentAuthenticate</b> interface provided in Windows Media Device Manager. Service providers and secure content providers must implement their own <b>IComponentAuthenticate</b> interface.

<b>CoCreateInstance</b> must be called first to acquire the <b>IComponentAuthenticate</b> interface.


#### Examples

The following C++ code authenticates the Windows Media Device Manager session and acquires the root object.


```cpp

// Authenticates the WMDM, and acquires an interface to the top-level object.
HRESULT MyClass::Authenticate()
{
    HRESULT hr;
    CComPtr<IComponentAuthenticate> pAuth;

    // Create the WMDM object and acquire 
    // its authentication interface.
    hr = CoCreateInstance(
        __uuidof(MediaDevMgr),
        NULL,
        CLSCTX_INPROC_SERVER,
        __uuidof(IComponentAuthenticate),
        (void**)&pAuth);

    if (hr != S_OK)
        return hr;

    // Create the secure channel client class needed to authenticate the application.
    // We'll use a global member variable to hold the secure channel client
    // in case we need to handle encryption, decryption, or MAC verification
    // during this session.
    m_pSAC = new CSecureChannelClient;
    if (m_pSAC == NULL)
        return E_FAIL;

    // Send the application's transfer certificate and the associated 
    // private key to the secure channel client.
    hr = m_pSAC->SetCertificate(
        SAC_CERT_V1,
        (BYTE *)abCert, sizeof(abCert),
        (BYTE *)abPVK,  sizeof(abPVK));
    if (hr != S_OK)
        return hr;
            
    // Send the authentication interface we created to the secure channel 
    // client and try authenticating the application with the V1 protocol.
    m_pSAC->SetInterface(pAuth);
    hr = m_pSAC->Authenticate(SAC_PROTOCOL_V1);
    if (hr != S_OK)
        return hr;

    // Authenticated succeeded, so we can use the WMDM.
    // Acquire an interface to the top-level WMDM interface.
    hr = pAuth->QueryInterface(__uuidof(IWMDeviceManager), (void**)&m_IWMDeviceMgr);


    return hr;
}

```

## -see-also

<a href="https://docs.microsoft.com/windows/desktop/WMDM/authenticating-the-application">Authenticating the Application</a>



<a href="https://docs.microsoft.com/windows/desktop/WMDM/csecurechannelclient-class">CSecureChannelClient Class</a>



<a href="https://docs.microsoft.com/windows/desktop/api/mswmdm/nn-mswmdm-icomponentauthenticate">IComponentAuthenticate Interface</a>



<a href="https://docs.microsoft.com/windows/desktop/WMDM/using-secure-authenticated-channels">Using Secure Authenticated Channels</a>

