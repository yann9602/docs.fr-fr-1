---
title: "IMetaDataEmit::SetPermissionSetProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPermissionSetProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34f2357de8d7ec522b4d10212eb82e351df8d152
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="a1289-102">IMetaDataEmit::SetPermissionSetProps, méthode</span><span class="sxs-lookup"><span data-stu-id="a1289-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="a1289-103">Définit ou met à jour des fonctionnalités de la signature de métadonnées d’un jeu d’autorisations défini par un appel antérieur à [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="a1289-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1289-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1289-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1289-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1289-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a1289-106">[in] Un jeton de métadonnées qui représente l’objet à être décorée.</span><span class="sxs-lookup"><span data-stu-id="a1289-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="a1289-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valeur qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a1289-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="a1289-108">[in] L’objet BLOB d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="a1289-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="a1289-109">[in] La taille, en octets, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="a1289-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="a1289-110">[out] Un `mdPermission` jeton de métadonnées qui représente les autorisations de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a1289-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1289-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1289-111">Requirements</span></span>  
 <span data-ttu-id="a1289-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1289-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1289-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a1289-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1289-114">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1289-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1289-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1289-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1289-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1289-116">See Also</span></span>  
 [<span data-ttu-id="a1289-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a1289-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a1289-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a1289-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
