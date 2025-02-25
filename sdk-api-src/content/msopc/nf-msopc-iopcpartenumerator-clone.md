---
UID: NF:msopc.IOpcPartEnumerator.Clone
title: IOpcPartEnumerator::Clone (msopc.h)
description: Creates a copy of the current enumerator and all its descendants.
helpviewer_keywords: ["Clone","Clone method [Open Packaging Conventions]","Clone method [Open Packaging Conventions]","IOpcPartEnumerator interface","IOpcPartEnumerator interface [Open Packaging Conventions]","Clone method","IOpcPartEnumerator.Clone","IOpcPartEnumerator::Clone","msopc/IOpcPartEnumerator::Clone","opc.iopcpartenumerator_clone"]
old-location: opc\iopcpartenumerator_clone.htm
tech.root: OPC
ms.assetid: b2719b6b-dcbd-4f8b-bb53-42114b95d6b3
ms.date: 12/05/2018
ms.keywords: Clone, Clone method [Open Packaging Conventions], Clone method [Open Packaging Conventions],IOpcPartEnumerator interface, IOpcPartEnumerator interface [Open Packaging Conventions],Clone method, IOpcPartEnumerator.Clone, IOpcPartEnumerator::Clone, msopc/IOpcPartEnumerator::Clone, opc.iopcpartenumerator_clone
req.header: msopc.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 7 [desktop apps only]
req.target-min-winversvr: Windows Server 2008 R2 [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: Opcobjectmodel.idl
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
 - IOpcPartEnumerator::Clone
 - msopc/IOpcPartEnumerator::Clone
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - msopc.h
api_name:
 - IOpcPartEnumerator.Clone
---

# IOpcPartEnumerator::Clone


## -description

Creates a copy of the current enumerator and all its descendants.

## -parameters

### -param copy [out, retval]

A pointer to the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpartenumerator">IOpcPartEnumerator</a> interface of the new enumerator.

## -returns

The method returns an <b>HRESULT</b>. Possible values include, but are not limited to, those in the following table.

<table>
<tr>
<th>Return code/value</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>S_OK</b></dt>
</dl>
</td>
<td width="60%">
The method succeeded.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>E_POINTER</b></dt>
</dl>
</td>
<td width="60%">
The <i>copy</i> parameter is <b>NULL</b>.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>OPC_E_ENUM_COLLECTION_CHANGED</b></dt>
<dt>0x80510050</dt>
</dl>
</td>
<td width="60%">
The enumerator is invalid because the underlying set has changed.

</td>
</tr>
</table>

## -remarks

When an enumerator is created, the current position precedes the first pointer. To set the current position to the first pointer of the enumerator, call the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartenumerator-movenext">MoveNext</a>method after creating the enumerator.


#### Thread Safety

Packaging objects are not thread-safe.

For more information, see the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-api-overview">Getting Started with the Packaging API</a>.

## -see-also

<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-api-overview">Getting Started with the Packaging API</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpartenumerator">IOpcPartEnumerator</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpartset">IOpcPartSet</a>



<b>Overviews</b>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-programming-reference">Packaging API Reference</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-programming-samples">Packaging API Samples</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-errors">Packaging Errors</a>



<b>Reference</b>

