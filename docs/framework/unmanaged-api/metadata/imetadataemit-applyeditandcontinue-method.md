---
title: "IMetaDataEmit::ApplyEditAndContinue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.ApplyEditAndContinue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4d6f378c4da884cffc6827f700586cee745642b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="d7a1e-102">IMetaDataEmit::ApplyEditAndContinue, méthode</span><span class="sxs-lookup"><span data-stu-id="d7a1e-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="d7a1e-103">La portée de l’assembly actuel des mises à jour avec les modifications apportées dans les métadonnées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d7a1e-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7a1e-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7a1e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7a1e-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="d7a1e-106">[in] Pointeur vers un <<!--zzxref:IUnknown --> `IUnknown`> objet qui représente les métadonnées delta à partir du fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="d7a1e-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="d7a1e-107">Les métadonnées delta sont le bloc de métadonnées qui inclut les modifications qui ont été apportées à la copie de métadonnées du module.</span><span class="sxs-lookup"><span data-stu-id="d7a1e-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a1e-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d7a1e-108">Requirements</span></span>  
 <span data-ttu-id="d7a1e-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a1e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a1e-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d7a1e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7a1e-111">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7a1e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7a1e-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a1e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a1e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7a1e-113">See Also</span></span>  
 [<span data-ttu-id="d7a1e-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d7a1e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d7a1e-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d7a1e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
