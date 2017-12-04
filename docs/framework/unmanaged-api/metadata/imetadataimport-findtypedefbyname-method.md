---
title: IMetaDataImport::FindTypeDefByName-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeDefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b3a5f9ff15e2b94e6d5c5e885605d8eabae711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="2d121-102">IMetaDataImport::FindTypeDefByName-Methode</span><span class="sxs-lookup"><span data-stu-id="2d121-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="2d121-103">Ruft einen Zeiger auf das TypeDef-Metadatentoken token für die <xref:System.Type> mit dem angegebenen Namen.</span><span class="sxs-lookup"><span data-stu-id="2d121-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d121-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2d121-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d121-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="2d121-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="2d121-106">[in] Der Name des Typs für die TypeDef-token abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="2d121-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="2d121-107">[in] Eine TypeDef oder TypeRef-Token, die die einschließende Klasse darstellt.</span><span class="sxs-lookup"><span data-stu-id="2d121-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="2d121-108">Wenn der zu ermittelnde Typ nicht um eine geschachtelte Klasse ist, wird dieser Wert auf NULL festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2d121-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="2d121-109">[out] Ein Zeiger auf das übereinstimmende TypeDef-Token.</span><span class="sxs-lookup"><span data-stu-id="2d121-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d121-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2d121-110">Requirements</span></span>  
 <span data-ttu-id="2d121-111">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d121-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d121-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d121-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d121-113">**Bibliothek:** als Ressource in MsCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="2d121-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d121-114">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d121-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d121-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2d121-115">See Also</span></span>  
 [<span data-ttu-id="2d121-116">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="2d121-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2d121-117">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="2d121-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)