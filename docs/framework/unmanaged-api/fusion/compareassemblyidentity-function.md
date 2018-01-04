---
title: CompareAssemblyIdentity, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266868a65a0db75b57d46d92a469b4b6ceaa88e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="65b54-102">CompareAssemblyIdentity, fonction</span><span class="sxs-lookup"><span data-stu-id="65b54-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="65b54-103">Compare deux identités d’assembly pour déterminer s’ils sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="65b54-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65b54-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65b54-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="65b54-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="65b54-106">[in] Identité textuelle du premier assembly de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="65b54-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="65b54-107">[in] Indicateur booléen qui indique l’unification de spécifié par l’utilisateur pour `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="65b54-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="65b54-108">[in] Identité textuelle du second assembly de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="65b54-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="65b54-109">[in] Indicateur booléen qui indique l’unification de spécifié par l’utilisateur pour `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="65b54-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="65b54-110">[out] Indicateur booléen qui indique si les deux assemblys sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="65b54-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="65b54-111">[out] Un [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) énumération qui contient des informations détaillées sur la comparaison.</span><span class="sxs-lookup"><span data-stu-id="65b54-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65b54-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="65b54-112">Return Value</span></span>  
 <span data-ttu-id="65b54-113">`pfEquivalent`Retourne une valeur booléenne qui indique si les deux assemblys sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="65b54-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="65b54-114">`pResult`Retourne l’une de le `AssemblyComparisonResult` valeurs, afin de donner une raison plus détaillée pour la valeur de `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="65b54-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65b54-115">Notes</span><span class="sxs-lookup"><span data-stu-id="65b54-115">Remarks</span></span>  
 <span data-ttu-id="65b54-116">`CompareAssemblyIdentity`vérifie si `pwzAssemblyIdentity1` et `pwzAssemblyIdentity2` sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="65b54-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="65b54-117">`pfEquivalent`a la valeur `true` sous un ou plusieurs des conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="65b54-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="65b54-118">Les identités des deux assemblys sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="65b54-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="65b54-119">Pour les assemblys à nom fort, l’équivalence implique le nom de l’assembly, version, jeton de clé publique et la culture sont identiques.</span><span class="sxs-lookup"><span data-stu-id="65b54-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="65b54-120">Pour les assemblys de nommés simple, l’équivalence implique une correspondance sur le nom de l’assembly et la culture.</span><span class="sxs-lookup"><span data-stu-id="65b54-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="65b54-121">Les deux identités d’assembly font référence aux assemblys qui s’exécutent sur le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65b54-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="65b54-122">Cette condition renvoie `true` même si les numéros de version d’assembly ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="65b54-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="65b54-123">Les deux assemblys ne sont pas des assemblys managés, mais `fUnified1` ou `fUnified2` a été défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="65b54-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="65b54-124">Le `fUnified` indicateur indique que tous les numéros de version au numéro de version de l’assembly à nom fort sont considérés comme équivalents à l’assembly de nom fort.</span><span class="sxs-lookup"><span data-stu-id="65b54-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="65b54-125">Par exemple, si la valeur de `pwzAssemblyIndentity1` est « MyAssembly, version = 3.0.0.0, culture = neutral, publicKeyToken =... » et la valeur de `fUnified1` est `true`, cela indique que toutes les versions de MyAssembly à partir de la version 0.0.0.0 à 3.0.0.0 doivent être traité comme équivalent.</span><span class="sxs-lookup"><span data-stu-id="65b54-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="65b54-126">Dans ce cas, si `pwzAssemblyIndentity2` fait référence au même assembly en tant que `pwzAssemblyIndentity1`, sauf qu’elle a un numéro de version inférieur, `pfEquivalent` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="65b54-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="65b54-127">Si `pwzAssemblyIdentity2` fait référence à un numéro de version supérieur, `pfEquivalent` a la valeur `true` uniquement si la valeur de `fUnified2` est `true`.</span><span class="sxs-lookup"><span data-stu-id="65b54-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="65b54-128">Le `pResult` paramètre inclut des informations spécifiques sur la raison pour laquelle les deux assemblys sont considérés comme équivalents ou pas.</span><span class="sxs-lookup"><span data-stu-id="65b54-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="65b54-129">Pour plus d’informations, consultez [AssemblyComparisonResult, énumération](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="65b54-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b54-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="65b54-130">Requirements</span></span>  
 <span data-ttu-id="65b54-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b54-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b54-132">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="65b54-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="65b54-133">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65b54-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65b54-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b54-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b54-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65b54-135">See Also</span></span>  
 [<span data-ttu-id="65b54-136">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="65b54-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="65b54-137">AssemblyComparisonResult, énumération</span><span class="sxs-lookup"><span data-stu-id="65b54-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
