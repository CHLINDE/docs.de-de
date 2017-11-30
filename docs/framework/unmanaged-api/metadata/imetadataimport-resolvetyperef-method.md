---
title: IMetaDataImport::ResolveTypeRef-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 390387abef5c48b4842adcfbfca126bb8292cc28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="18dc7-102">IMetaDataImport::ResolveTypeRef-Methode</span><span class="sxs-lookup"><span data-stu-id="18dc7-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="18dc7-103">Löst ein <xref:System.Type> Verweis durch das angegebene TypeRef-Token dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="18dc7-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18dc7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="18dc7-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18dc7-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="18dc7-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="18dc7-106">[in] Das TypeRef-Metadatentoken, Informationen zu den referenzierten Typ zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="18dc7-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="18dc7-107">[in] Die IID der Schnittstelle im zurückzugebenden `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="18dc7-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="18dc7-108">In der Regel ist dies IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="18dc7-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="18dc7-109">[out] Eine Schnittstelle zu des Geltungsbereichs des Moduls, in dem der referenzierte Typ definiert ist.</span><span class="sxs-lookup"><span data-stu-id="18dc7-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="18dc7-110">[out] Ein Zeiger auf ein TypeDef-Token, das den Verweistyp darstellt.</span><span class="sxs-lookup"><span data-stu-id="18dc7-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18dc7-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="18dc7-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18dc7-112">Verwenden Sie diese Methode nicht, wenn mehrere Anwendungsdomänen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="18dc7-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="18dc7-113">Die Methode berücksichtigt nicht die Grenzen von Anwendungsdomänen hinweg.</span><span class="sxs-lookup"><span data-stu-id="18dc7-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="18dc7-114">Wenn mehrere Versionen einer Assembly geladen werden, und sie den gleichen Typ mit dem gleichen Namespace enthalten, gibt die Methode des Geltungsbereichs des Moduls des ersten gefundenen Typs zurück.</span><span class="sxs-lookup"><span data-stu-id="18dc7-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="18dc7-115">Die `ResolveTypeRef` Methode sucht die Typdefinition in anderen Modulen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="18dc7-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="18dc7-116">Wenn die Typdefinition gefunden wird, `ResolveTypeRef` gibt eine Schnittstelle, Modulbereich sowie das TypeDef-Token für den Typ zurück.</span><span class="sxs-lookup"><span data-stu-id="18dc7-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="18dc7-117">Der Typverweis aufgelöst werden besitzt einen Auflösungsbereich von AssemblyRef, die `ResolveTypeRef` Methode sucht eine Übereinstimmung nur in den Metadatenbereichen, die bereits mit Aufrufen von entweder geöffnet wurden die [IMetaDataDispenser:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)Methode oder die [IMetaDataDispenser:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) Methode.</span><span class="sxs-lookup"><span data-stu-id="18dc7-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="18dc7-118">Grund hierfür ist, `ResolveTypeRef` kann nicht bestimmt werden nur die AssemblyRef des Gültigkeitsbereichs, in dem auf einem Datenträger oder im globalen Assemblycache die Assembly gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="18dc7-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18dc7-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="18dc7-119">Requirements</span></span>  
 <span data-ttu-id="18dc7-120">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18dc7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18dc7-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18dc7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18dc7-122">**Bibliothek:** als Ressource in MsCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="18dc7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18dc7-123">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18dc7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18dc7-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="18dc7-124">See Also</span></span>  
 [<span data-ttu-id="18dc7-125">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="18dc7-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="18dc7-126">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="18dc7-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)