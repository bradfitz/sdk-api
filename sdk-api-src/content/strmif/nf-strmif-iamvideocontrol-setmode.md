---
UID: NF:strmif.IAMVideoControl.SetMode
title: IAMVideoControl::SetMode (strmif.h)
description: The SetMode method sets the video control mode of operation.
helpviewer_keywords: ["IAMVideoControl interface [DirectShow]","SetMode method","IAMVideoControl.SetMode","IAMVideoControl::SetMode","IAMVideoControlSetMode","SetMode","SetMode method [DirectShow]","SetMode method [DirectShow]","IAMVideoControl interface","dshow.iamvideocontrol_setmode","strmif/IAMVideoControl::SetMode"]
old-location: dshow\iamvideocontrol_setmode.htm
tech.root: dshow
ms.assetid: 09fe5d3f-41d8-4a60-a770-64c628a6b82d
ms.date: 12/05/2018
ms.keywords: IAMVideoControl interface [DirectShow],SetMode method, IAMVideoControl.SetMode, IAMVideoControl::SetMode, IAMVideoControlSetMode, SetMode, SetMode method [DirectShow], SetMode method [DirectShow],IAMVideoControl interface, dshow.iamvideocontrol_setmode, strmif/IAMVideoControl::SetMode
req.header: strmif.h
req.include-header: Dshow.h
req.target-type: Windows
req.target-min-winverclnt: Windows 2000 Professional [desktop apps only]
req.target-min-winversvr: Windows 2000 Server [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Strmiids.lib
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - IAMVideoControl::SetMode
 - strmif/IAMVideoControl::SetMode
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - Strmiids.lib
 - Strmiids.dll
api_name:
 - IAMVideoControl.SetMode
---

# IAMVideoControl::SetMode


## -description

The <code>SetMode</code> method sets the video control mode of operation.

## -parameters

### -param pPin [in]

Pointer to the pin to set the video control mode on.

### -param Mode [in]

Value specifying a combination of the flags from the [VideoControlFlags](https://docs.microsoft.com/windows/desktop/api/strmif/ne-strmif-videocontrolflags) enumeration to set the video control mode.

## -returns

Returns an <b>HRESULT</b> value that depends on the implementation of the interface.

## -remarks

Possible modes of operation include one or more of the following: flipping the picture horizontally, flipping the picture vertically, enabling external triggers, and simulating external triggers.

## -see-also

<a href="https://docs.microsoft.com/windows/desktop/DirectShow/error-and-success-codes">Error and Success Codes</a>



<a href="https://docs.microsoft.com/windows/desktop/api/strmif/nn-strmif-iamvideocontrol">IAMVideoControl Interface</a>

