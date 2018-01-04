---
title: "IMetaDataEmit::DefineModuleRef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineModuleRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b745e216ca49ed5d226d6d531281880b43e4939
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="e63db-102">IMetaDataEmit::DefineModuleRef, méthode</span><span class="sxs-lookup"><span data-stu-id="e63db-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="e63db-103">Crée la signature de métadonnées pour un module avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="e63db-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e63db-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e63db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e63db-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e63db-106">[in] Le nom de l’autre fichier de métadonnées, en général une DLL.</span><span class="sxs-lookup"><span data-stu-id="e63db-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="e63db-107">Il s’agit du nom de fichier uniquement.</span><span class="sxs-lookup"><span data-stu-id="e63db-107">This is the file name only.</span></span> <span data-ttu-id="e63db-108">N’utilisez pas un nom de chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="e63db-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="e63db-109">[out] Assigné `mdModuleRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="e63db-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e63db-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e63db-110">Requirements</span></span>  
 <span data-ttu-id="e63db-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e63db-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e63db-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e63db-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e63db-113">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e63db-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e63db-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e63db-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63db-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e63db-115">See Also</span></span>  
 [<span data-ttu-id="e63db-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e63db-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e63db-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e63db-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
