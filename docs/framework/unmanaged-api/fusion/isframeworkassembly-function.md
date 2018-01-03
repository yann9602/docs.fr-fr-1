---
title: IsFrameworkAssembly, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa077ce13031772ec2ea20708c1dbd29da02d32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="2545d-102">IsFrameworkAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="2545d-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="2545d-103">Obtient une valeur qui indique si l’assembly spécifié est géré.</span><span class="sxs-lookup"><span data-stu-id="2545d-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2545d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2545d-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2545d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2545d-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="2545d-106">[in] Le nom de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="2545d-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="2545d-107">[out] Valeur booléenne qui indique si l’assembly est géré.</span><span class="sxs-lookup"><span data-stu-id="2545d-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="2545d-108">[in] Chaîne non canonique qui contient l’identité unique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2545d-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="2545d-109">[in] Taille de `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2545d-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2545d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2545d-110">Remarks</span></span>  
 <span data-ttu-id="2545d-111">Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="2545d-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="2545d-112">Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une valeur booléenne `true`.</span><span class="sxs-lookup"><span data-stu-id="2545d-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="2545d-113">Si l’assembly nommé n’est pas partie du .NET Framework, ou si le `pwzAssemblyReference` paramètre ne désigne pas un assembly, `pbIsFrameworkAssembly` contient une valeur booléenne `false`.</span><span class="sxs-lookup"><span data-stu-id="2545d-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2545d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2545d-114">Requirements</span></span>  
 <span data-ttu-id="2545d-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2545d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2545d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2545d-116">See Also</span></span>  
 [<span data-ttu-id="2545d-117">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="2545d-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
