---
title: "IMetaDataTables::GetBlobHeapSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetBlobHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 176d924ec117365408a31f1bfc38901a7ef2cf65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="440a7-102">IMetaDataTables::GetBlobHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="440a7-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="440a7-103">Obtient la taille, en octets, du tas de l’objet binaire volumineux (BLOB).</span><span class="sxs-lookup"><span data-stu-id="440a7-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="440a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="440a7-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="440a7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="440a7-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="440a7-106">[out] Pointeur vers la taille, en octets, du tas de BLOB.</span><span class="sxs-lookup"><span data-stu-id="440a7-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="440a7-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="440a7-107">Requirements</span></span>  
 <span data-ttu-id="440a7-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="440a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="440a7-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="440a7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="440a7-110">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="440a7-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="440a7-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="440a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="440a7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="440a7-112">See Also</span></span>  
 [<span data-ttu-id="440a7-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="440a7-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="440a7-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="440a7-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
