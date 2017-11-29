---
title: "IMetaDataTables::GetStringHeapSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetStringHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a0e664192ac39dd12085346738dbc283a11d3381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="3f93a-102">IMetaDataTables::GetStringHeapSize, méthode</span><span class="sxs-lookup"><span data-stu-id="3f93a-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="3f93a-103">Obtient la taille, en octets, du tas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="3f93a-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f93a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f93a-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f93a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f93a-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="3f93a-106">[out] Pointeur vers la taille, en octets, du tas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="3f93a-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f93a-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f93a-107">Requirements</span></span>  
 <span data-ttu-id="3f93a-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f93a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f93a-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f93a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f93a-110">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f93a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f93a-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f93a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f93a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f93a-112">See Also</span></span>  
 [<span data-ttu-id="3f93a-113">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f93a-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="3f93a-114">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f93a-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
