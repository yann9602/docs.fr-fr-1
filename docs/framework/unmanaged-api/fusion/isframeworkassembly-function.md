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
ms.openlocfilehash: 216a7221550cb6345b29b5ed9e45b13ce40eadf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="10ca7-102">IsFrameworkAssembly, fonction</span><span class="sxs-lookup"><span data-stu-id="10ca7-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="10ca7-103">Obtient une valeur qui indique si l’assembly spécifié est géré.</span><span class="sxs-lookup"><span data-stu-id="10ca7-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ca7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10ca7-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10ca7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10ca7-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="10ca7-106">[in] Le nom de l’assembly à vérifier.</span><span class="sxs-lookup"><span data-stu-id="10ca7-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="10ca7-107">[out] Valeur booléenne qui indique si l’assembly est géré.</span><span class="sxs-lookup"><span data-stu-id="10ca7-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="10ca7-108">[in] Chaîne non canonique qui contient l’identité unique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="10ca7-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="10ca7-109">[in] Taille de `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="10ca7-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10ca7-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="10ca7-110">Remarks</span></span>  
 <span data-ttu-id="10ca7-111">Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="10ca7-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="10ca7-112">Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une valeur booléenne `true`.</span><span class="sxs-lookup"><span data-stu-id="10ca7-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="10ca7-113">Si l’assembly nommé n’est pas partie du .NET Framework, ou si le `pwzAssemblyReference` paramètre ne désigne pas un assembly, `pbIsFrameworkAssembly` contient une valeur booléenne `false`.</span><span class="sxs-lookup"><span data-stu-id="10ca7-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10ca7-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="10ca7-114">Requirements</span></span>  
 <span data-ttu-id="10ca7-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10ca7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ca7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10ca7-116">See Also</span></span>  
 [<span data-ttu-id="10ca7-117">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="10ca7-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
