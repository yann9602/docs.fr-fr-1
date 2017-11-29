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
ms.openlocfilehash: 3c7709180e5b7811379c25977f8a8d23b91adb3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="fa09e-102">IMetaDataImport::EnumUnresolvedMethods, méthode</span><span class="sxs-lookup"><span data-stu-id="fa09e-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="fa09e-103">Énumère les jetons MemberDef représentant les méthodes non résolues dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="fa09e-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa09e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa09e-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa09e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fa09e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fa09e-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="fa09e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="fa09e-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fa09e-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="fa09e-108">[out] Tableau utilisé pour stocker les jetons MemberDef.</span><span class="sxs-lookup"><span data-stu-id="fa09e-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fa09e-109">[in] Taille maximale du tableau `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="fa09e-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fa09e-110">[out] Le nombre de jetons MemberDef retournés dans `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="fa09e-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa09e-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fa09e-111">Return Value</span></span>  
  
|<span data-ttu-id="fa09e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa09e-112">HRESULT</span></span>|<span data-ttu-id="fa09e-113">Description</span><span class="sxs-lookup"><span data-stu-id="fa09e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fa09e-114">`EnumUnresolvedMethods`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fa09e-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fa09e-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="fa09e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="fa09e-116">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="fa09e-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa09e-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="fa09e-117">Remarks</span></span>  
 <span data-ttu-id="fa09e-118">Une méthode non résolue est celle qui a été déclarée, mais ne pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="fa09e-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="fa09e-119">Une méthode est incluse dans l’énumération si la méthode est marquée `miForwardRef` et `mdPinvokeImpl` ou `miRuntime` est défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="fa09e-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="fa09e-120">En d’autres termes, une méthode non résolue est une méthode de classe qui est marquée `miForwardRef` mais qui n’est pas implémenté en code non managé (atteint via PInvoke) ni implémenté en interne par le runtime lui-même</span><span class="sxs-lookup"><span data-stu-id="fa09e-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="fa09e-121">L’énumération exclut toutes les méthodes qui sont définies au niveau de la portée du module (globales) ou dans des interfaces ou des classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="fa09e-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa09e-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fa09e-122">Requirements</span></span>  
 <span data-ttu-id="fa09e-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa09e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa09e-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa09e-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa09e-125">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa09e-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa09e-126">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa09e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa09e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa09e-127">See Also</span></span>  
 [<span data-ttu-id="fa09e-128">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="fa09e-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fa09e-129">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="fa09e-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
