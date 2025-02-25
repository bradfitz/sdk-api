---
UID: NF:wdstptmgmt.IWdsTransportServer.DisconnectClient
title: IWdsTransportServer::DisconnectClient (wdstptmgmt.h)
description: Disconnects a WDS client from a transport session and specifies what action the WDS client should take upon disconnection.
helpviewer_keywords: ["DisconnectClient","DisconnectClient method [Windows Deployment Services]","DisconnectClient method [Windows Deployment Services]","IWdsTransportServer interface","IWdsTransportServer interface [Windows Deployment Services]","DisconnectClient method","IWdsTransportServer.DisconnectClient","IWdsTransportServer::DisconnectClient","wds.iwdstransportserver_disconnectclient","wdstptmgmt/IWdsTransportServer::DisconnectClient"]
old-location: wds\iwdstransportserver_disconnectclient.htm
tech.root: wds
ms.assetid: 7ab63f7e-1840-40d1-8933-ea92042aaced
ms.date: 12/05/2018
ms.keywords: DisconnectClient, DisconnectClient method [Windows Deployment Services], DisconnectClient method [Windows Deployment Services],IWdsTransportServer interface, IWdsTransportServer interface [Windows Deployment Services],DisconnectClient method, IWdsTransportServer.DisconnectClient, IWdsTransportServer::DisconnectClient, wds.iwdstransportserver_disconnectclient, wdstptmgmt/IWdsTransportServer::DisconnectClient
req.header: wdstptmgmt.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: None supported
req.target-min-winversvr: Windows Server 2008 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: Wdstptmgmt.tlb
req.lib: 
req.dll: Wdstptmgmt.dll
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - IWdsTransportServer::DisconnectClient
 - wdstptmgmt/IWdsTransportServer::DisconnectClient
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - Wdstptmgmt.dll
api_name:
 - IWdsTransportServer.DisconnectClient
---

# IWdsTransportServer::DisconnectClient


## -description

Disconnects a WDS client from a transport session and specifies what action the WDS client should take upon disconnection.

## -parameters

### -param ulClientId

A unique ID for the WDS that was generated by the WDS transport server.

### -param DisconnectionType

A value of the <a href="/windows/win32/api/wdstptmgmt/ne-wdstptmgmt-wdstransport_disconnect_type">WDSTRANSPORT_DISCONNECT_TYPE</a> enumeration that specifies what action the WDS client should take upon disconnection from the WDS server.

## -returns

Standard HRESULT error values are used: S_OK for success; others for failure.

## -see-also

<a href="https://docs.microsoft.com/windows/desktop/api/wdstptmgmt/nn-wdstptmgmt-iwdstransportserver">IWdsTransportServer</a>



<a href="/windows/win32/api/wdstptmgmt/ne-wdstptmgmt-wdstransport_disconnect_type">WDSTRANSPORT_DISCONNECT_TYPE</a>

