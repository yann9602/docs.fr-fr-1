---
title: "IMetaDataTables::GetGuid, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58dbcb7ebf56f126d89a42a1f5df6247266cb38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="14ca8-102">IMetaDataTables::GetGuid, méthode</span><span class="sxs-lookup"><span data-stu-id="14ca8-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="14ca8-103">Obtient un GUID à partir de la ligne à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="14ca8-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ca8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14ca8-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14ca8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="14ca8-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="14ca8-106">[in] L’index de la ligne à partir de laquelle obtenir le GUID.</span><span class="sxs-lookup"><span data-stu-id="14ca8-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="14ca8-107">[out] Pointeur vers un pointeur vers le GUID.</span><span class="sxs-lookup"><span data-stu-id="14ca8-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14ca8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="14ca8-108">Remarks</span></span>  
 <span data-ttu-id="14ca8-109">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="14ca8-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="14ca8-110">Pour plus d’informations sur la table GUID, consultez la documentation du Common Language Infrastructure (CLI), en particulier « Partition II : Metadata Definition et Semantics ».</span><span class="sxs-lookup"><span data-stu-id="14ca8-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="14ca8-111">La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.</span><span class="sxs-lookup"><span data-stu-id="14ca8-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14ca8-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="14ca8-112">Requirements</span></span>  
 <span data-ttu-id="14ca8-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ca8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ca8-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14ca8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14ca8-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14ca8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14ca8-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14ca8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ca8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14ca8-117">See Also</span></span>  
 [<span data-ttu-id="14ca8-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="14ca8-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="14ca8-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="14ca8-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
