---
title: "IMetaDataTables::GetUserStringHeapSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetUserStringHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b1f4f1b8c3cafb28c2b84867dbe5ac3f8424e8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="4f15f-102">IMetaDataTables::GetUserStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="4f15f-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="4f15f-103">Obtient la taille, en octets, du tas de chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4f15f-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f15f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f15f-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f15f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f15f-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="4f15f-106">[out] Pointeur vers la taille, en octets, du tas de chaîne utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4f15f-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f15f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4f15f-107">Requirements</span></span>  
 <span data-ttu-id="4f15f-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f15f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f15f-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f15f-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f15f-110">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f15f-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f15f-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f15f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f15f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f15f-112">See Also</span></span>  
 [<span data-ttu-id="4f15f-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="4f15f-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="4f15f-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="4f15f-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
