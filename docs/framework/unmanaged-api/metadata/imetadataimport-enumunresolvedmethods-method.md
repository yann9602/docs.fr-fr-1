---
title: "IMetaDataImport::EnumUnresolvedMethods, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4e77453fc11b77b602d4a89f0d90540c06b0a08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="35453-102">IMetaDataImport::EnumUnresolvedMethods, méthode</span><span class="sxs-lookup"><span data-stu-id="35453-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="35453-103">Énumère les jetons MemberDef représentant les méthodes non résolues dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="35453-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35453-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35453-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35453-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35453-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="35453-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="35453-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="35453-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="35453-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="35453-108">[out] Tableau utilisé pour stocker les jetons MemberDef.</span><span class="sxs-lookup"><span data-stu-id="35453-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="35453-109">[in] Taille maximale du tableau `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="35453-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="35453-110">[out] Le nombre de jetons MemberDef retournés dans `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="35453-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35453-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="35453-111">Return Value</span></span>  
  
|<span data-ttu-id="35453-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35453-112">HRESULT</span></span>|<span data-ttu-id="35453-113">Description</span><span class="sxs-lookup"><span data-stu-id="35453-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="35453-114">`EnumUnresolvedMethods`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="35453-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="35453-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="35453-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="35453-116">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="35453-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35453-117">Notes</span><span class="sxs-lookup"><span data-stu-id="35453-117">Remarks</span></span>  
 <span data-ttu-id="35453-118">Une méthode non résolue est celle qui a été déclarée, mais ne pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="35453-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="35453-119">Une méthode est incluse dans l’énumération si la méthode est marquée `miForwardRef` et `mdPinvokeImpl` ou `miRuntime` est défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="35453-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="35453-120">En d’autres termes, une méthode non résolue est une méthode de classe qui est marquée `miForwardRef` mais qui n’est pas implémenté en code non managé (atteint via PInvoke) ni implémenté en interne par le runtime lui-même</span><span class="sxs-lookup"><span data-stu-id="35453-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="35453-121">L’énumération exclut toutes les méthodes qui sont définies au niveau de la portée du module (globales) ou dans des interfaces ou des classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="35453-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35453-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35453-122">Requirements</span></span>  
 <span data-ttu-id="35453-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35453-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35453-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="35453-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35453-125">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35453-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35453-126">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35453-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35453-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35453-127">See Also</span></span>  
 [<span data-ttu-id="35453-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="35453-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="35453-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="35453-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
