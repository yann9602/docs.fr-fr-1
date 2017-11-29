---
title: "IMetaDataEmit::DefinePermissionSet, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePermissionSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a503f22710f392ecbb0ae2704d2c2950a858c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="001de-102">IMetaDataEmit::DefinePermissionSet, méthode</span><span class="sxs-lookup"><span data-stu-id="001de-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="001de-103">Crée une définition pour un jeu d’autorisations avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="001de-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="001de-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="001de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="001de-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="001de-106">[in] Objet à être décorée.</span><span class="sxs-lookup"><span data-stu-id="001de-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="001de-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valeur qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="001de-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="001de-108">[in] L’objet BLOB d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="001de-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="001de-109">[in] La taille, en octets, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="001de-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="001de-110">[out] Le jeton d’autorisations retourné.</span><span class="sxs-lookup"><span data-stu-id="001de-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="001de-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="001de-111">Requirements</span></span>  
 <span data-ttu-id="001de-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="001de-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="001de-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="001de-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="001de-114">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="001de-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="001de-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="001de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001de-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="001de-116">See Also</span></span>  
 [<span data-ttu-id="001de-117">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="001de-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="001de-118">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="001de-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
