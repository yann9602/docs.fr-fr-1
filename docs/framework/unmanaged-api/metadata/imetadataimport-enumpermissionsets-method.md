---
title: "IMetaDataImport::EnumPermissionSets, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumPermissionSets
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f31d35f21a16983b6ab9c23f1f65c3916b5138d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="880da-102">IMetaDataImport::EnumPermissionSets, méthode</span><span class="sxs-lookup"><span data-stu-id="880da-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="880da-103">Énumère les autorisations pour les objets inclus dans une portée des métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="880da-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="880da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="880da-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="880da-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="880da-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="880da-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="880da-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="880da-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="880da-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="880da-108">[in] Un jeton de métadonnées qui limite l’étendue de la recherche, ou NULL pour la recherche la plus large possible.</span><span class="sxs-lookup"><span data-stu-id="880da-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="880da-109">[in] Indicateurs représentant le <xref:System.Security.Permissions.SecurityAction> valeurs à inclure dans `rPermission`, ou zéro pour retourner toutes les actions.</span><span class="sxs-lookup"><span data-stu-id="880da-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="880da-110">[out] Tableau utilisé pour stocker les jetons d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="880da-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="880da-111">[in] Taille maximale du tableau `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="880da-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="880da-112">[out] Le nombre de jetons Permission retournés dans `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="880da-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="880da-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="880da-113">Return Value</span></span>  
  
|<span data-ttu-id="880da-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="880da-114">HRESULT</span></span>|<span data-ttu-id="880da-115">Description</span><span class="sxs-lookup"><span data-stu-id="880da-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="880da-116">`EnumPermissionSets`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="880da-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="880da-117">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="880da-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="880da-118">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="880da-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="880da-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="880da-119">Requirements</span></span>  
 <span data-ttu-id="880da-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="880da-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="880da-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="880da-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="880da-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="880da-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="880da-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="880da-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880da-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="880da-124">See Also</span></span>  
 [<span data-ttu-id="880da-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="880da-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="880da-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="880da-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
