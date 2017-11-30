---
title: "IMetaDataEmit::Save, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Save
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a2e77ad9ce66a04ef0530dc41f9795c501eed9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="149aa-102">IMetaDataEmit::Save, méthode</span><span class="sxs-lookup"><span data-stu-id="149aa-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="149aa-103">Enregistre toutes les métadonnées dans la portée actuelle dans le fichier à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="149aa-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="149aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="149aa-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="149aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="149aa-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="149aa-106">[in] Le nom du fichier de destination.</span><span class="sxs-lookup"><span data-stu-id="149aa-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="149aa-107">Si cette valeur est null, la copie en mémoire sera enregistrée dans le dernier emplacement qui a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="149aa-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="149aa-108">[in] Réservé.</span><span class="sxs-lookup"><span data-stu-id="149aa-108">[in] Reserved.</span></span> <span data-ttu-id="149aa-109">Doit être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="149aa-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="149aa-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="149aa-110">Requirements</span></span>  
 <span data-ttu-id="149aa-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="149aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="149aa-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="149aa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="149aa-113">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="149aa-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="149aa-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="149aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149aa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="149aa-115">See Also</span></span>  
 [<span data-ttu-id="149aa-116">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="149aa-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="149aa-117">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="149aa-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
