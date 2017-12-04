---
title: IMetaDataDispenserEx-Schnittstelle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ecb4e94c0deed3ed62b2d2eb8b0309ca092abf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="8e030-102">IMetaDataDispenserEx-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8e030-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="8e030-103">Erweitert die [IMetaDataDispenser-Schnittstelle](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) Schnittstelle bieten die Möglichkeit zum Steuern, wie die Metadaten-APIs im aktuellen Metadatenbereich ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8e030-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e030-104">Methoden</span><span class="sxs-lookup"><span data-stu-id="8e030-104">Methods</span></span>  
  
|<span data-ttu-id="8e030-105">Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-105">Method</span></span>|<span data-ttu-id="8e030-106">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8e030-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e030-107">FindAssembly-Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="8e030-108">Diese Methode ist nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="8e030-108">This method is not implemented.</span></span> <span data-ttu-id="8e030-109">Wenn Sie aufgerufen wird, wird E_NOTIMPL zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8e030-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="8e030-110">FindAssemblyModule-Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="8e030-111">Diese Methode ist nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="8e030-111">This method is not implemented.</span></span> <span data-ttu-id="8e030-112">Wenn Sie aufgerufen wird, wird E_NOTIMPL zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8e030-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="8e030-113">GetCORSystemDirectory-Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="8e030-114">Ruft das Verzeichnis, das die aktuelle common Language Runtime (CLR) enthält.</span><span class="sxs-lookup"><span data-stu-id="8e030-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="8e030-115">Diese Methode ist nur für die Verwendung von Out-of-Process-Debugger unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8e030-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="8e030-116">Wenn aus einer anderen Komponente aufgerufen wird, gibt es E_NOTIMPL zurück.</span><span class="sxs-lookup"><span data-stu-id="8e030-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="8e030-117">GetOption-Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="8e030-118">Ruft den Wert der angegebenen Option für den aktuellen Metadatenbereich ab.</span><span class="sxs-lookup"><span data-stu-id="8e030-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="8e030-119">Die Option wird gesteuert, wie Aufrufe im aktuellen Metadatenbereich behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="8e030-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="8e030-120">OpenScopeOnITypeInfo-Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="8e030-121">Diese Methode ist nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="8e030-121">This method is not implemented.</span></span> <span data-ttu-id="8e030-122">Wenn Sie aufgerufen wird, wird E_NOTIMPL zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8e030-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="8e030-123">SetOption-Methode</span><span class="sxs-lookup"><span data-stu-id="8e030-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="8e030-124">Legt die angegebene Option auf einen angegebenen Wert für den aktuellen Metadatenbereich fest.</span><span class="sxs-lookup"><span data-stu-id="8e030-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="8e030-125">Die Option wird gesteuert, wie Aufrufe im aktuellen Metadatenbereich behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="8e030-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e030-126">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8e030-126">Requirements</span></span>  
 <span data-ttu-id="8e030-127">**Plattform:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e030-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e030-128">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8e030-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e030-129">**Bibliothek:** als Ressource in MsCorEE.dll verwendet</span><span class="sxs-lookup"><span data-stu-id="8e030-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e030-130">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e030-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e030-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8e030-131">See Also</span></span>  
 [<span data-ttu-id="8e030-132">Metadatenschnittstellen</span><span class="sxs-lookup"><span data-stu-id="8e030-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="8e030-133">IMetaDataDispenser-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8e030-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="8e030-134">IMetaDataEmit-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8e030-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8e030-135">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="8e030-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)