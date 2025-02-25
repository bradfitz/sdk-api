---
UID: NN:msopc.IOpcPartSet
title: IOpcPartSet (msopc.h)
description: An unordered set of IOpcPart interface pointers to part objects that represent the parts in a package that are not Relationships parts.
helpviewer_keywords: ["IOpcPartSet","IOpcPartSet interface [Open Packaging Conventions]","IOpcPartSet interface [Open Packaging Conventions]","described","msopc/IOpcPartSet","opc.iopcpartset"]
old-location: opc\iopcpartset.htm
tech.root: OPC
ms.assetid: f34c682f-7677-4d20-bd37-b1a68293d85c
ms.date: 12/05/2018
ms.keywords: IOpcPartSet, IOpcPartSet interface [Open Packaging Conventions], IOpcPartSet interface [Open Packaging Conventions],described, msopc/IOpcPartSet, opc.iopcpartset
req.header: msopc.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 7 [desktop apps \| UWP apps]
req.target-min-winversvr: Windows Server 2008 R2 [desktop apps \| UWP apps]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: Msopc.idl
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
 - IOpcPartSet
 - msopc/IOpcPartSet
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
 - IOpcPartSet
---

# IOpcPartSet interface


## -description

An unordered set of <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface pointers to part objects that represent the parts in a package that are not Relationships parts.

## -inheritance

The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IOpcPartSet</b> interface inherits from the <a href="https://docs.microsoft.com/windows/desktop/api/unknwn/nn-unknwn-iunknown">IUnknown</a> interface. <b>IOpcPartSet</b> also has these types of members:
<ul>
<li><a href="https://docs.microsoft.com/">Methods</a></li>
</ul>

## -members

The <b>IOpcPartSet</b> interface has these methods.
<table class="members" id="memberListMethods">
<tr>
<th align="left" width="37%">Method</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-createpart">CreatePart</a>
</td>
<td align="left" width="63%">
Creates a part object that represents a part and adds a pointer to the object's <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface to the set.

</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-deletepart">DeletePart</a>
</td>
<td align="left" width="63%">
Deletes the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface pointer of a specified part object from the set.

</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-getenumerator">GetEnumerator</a>
</td>
<td align="left" width="63%">
Gets an enumerator of <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface pointers  in the set.

</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-getpart">GetPart</a>
</td>
<td align="left" width="63%">
Gets a part object, which represents a specified part, in the set.

</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-partexists">PartExists</a>
</td>
<td align="left" width="63%">
Gets a value that indicates whether a specified part is represented as a part object in the set.

</td>
</tr>
</table>

## -remarks

To retrieve the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface pointer of the part object that represents a specific part, call the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-partexists">PartExists</a> method and pass in the part name to confirm that the part is represented in the set. If it is, call the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-getpart">GetPart</a> method and pass in the part name to retrieve the <b>IOpcPart</b> interface pointer.

The <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nf-msopc-iopcpartset-createpart">CreatePart</a> method cannot create a part object that represents a Relationships part.

When a package that is represented as a package object is serialized, only the parts that are represented by part objects with <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface pointers included in the set are serialized with the package.

If a part is not represented by a part object in the set when the package is serialized, that part will not be serialized with the package.

When a part object is created and a pointer to it is added to the set, the part it represents is serialized when the package is serialized.

When an  <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> interface pointer is deleted from the set, the part it represents is not serialized when the package is serialized.

An <a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpart">IOpcPart</a> provides access to the properties of the part. For details about these properties, see the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/parts-overview">Parts Overview</a> and <b>IOpcPart</b>.


#### Thread Safety

Packaging objects are not thread-safe.

For more information, see the <a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-api-overview">Getting Started with the Packaging API</a>.

## -see-also

<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/core-packaging-interfaces">Core Packaging Interfaces</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-api-overview">Getting Started with the Packaging API</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/api/msopc/nn-msopc-iopcpartenumerator">IOpcPartEnumerator</a>



<b>Overviews</b>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-programming-reference">Packaging API Reference</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/packaging-programming-samples">Packaging API Samples</a>



<a href="https://docs.microsoft.com/previous-versions/windows/desktop/opc/parts-overview">Parts Overview</a>



<b>Reference</b>

