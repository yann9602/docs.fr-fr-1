---
title: "IMetaDataTables::GetNextString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9d9062ef164c5a50652ed78786725967fda999d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="a13e1-102">IMetaDataTables::GetNextString, méthode</span><span class="sxs-lookup"><span data-stu-id="a13e1-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="a13e1-103">Obtient l’index de la chaîne suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="a13e1-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a13e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a13e1-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a13e1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a13e1-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="a13e1-106">[in] La valeur d’index d’une colonne de table de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a13e1-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="a13e1-107">[out] Pointeur vers l’index de la chaîne suivante dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="a13e1-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a13e1-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a13e1-108">Requirements</span></span>  
 <span data-ttu-id="a13e1-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a13e1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a13e1-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a13e1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a13e1-111">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a13e1-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a13e1-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a13e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13e1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a13e1-113">See Also</span></span>  
 [<span data-ttu-id="a13e1-114">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="a13e1-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="a13e1-115">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="a13e1-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
