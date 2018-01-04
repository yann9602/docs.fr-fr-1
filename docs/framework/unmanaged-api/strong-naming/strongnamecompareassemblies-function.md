---
title: StrongNameCompareAssemblies, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameCompareAssemblies
helpviewer_keywords: StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed98b1713427a71c73c30ddd64188f61d51045c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="03695-102">StrongNameCompareAssemblies, fonction</span><span class="sxs-lookup"><span data-stu-id="03695-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="03695-103">Détermine si deux assemblys diffèrent uniquement par leurs signatures de nom fort.</span><span class="sxs-lookup"><span data-stu-id="03695-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="03695-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="03695-104">This function has been deprecated.</span></span> <span data-ttu-id="03695-105">Utilisez le [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="03695-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03695-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03695-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03695-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="03695-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="03695-108">[in] Le chemin d’accès à l’assembly en premier.</span><span class="sxs-lookup"><span data-stu-id="03695-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="03695-109">[in] Le chemin d’accès au deuxième assembly.</span><span class="sxs-lookup"><span data-stu-id="03695-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="03695-110">[out] Une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="03695-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="03695-111">`SN_CMP_DIFFERENT`(0) - Spécifie que les assemblys contiennent des données différentes.</span><span class="sxs-lookup"><span data-stu-id="03695-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="03695-112">`SN_CMP_IDENTICAL`(1) - Spécifie que les assemblys sont exactement les mêmes, y compris leurs signatures et la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="03695-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="03695-113">`SN_CMP_SIGONLY`(2) - Spécifie que les assemblys diffèrent uniquement par leur signature et de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="03695-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03695-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="03695-114">Return Value</span></span>  
 <span data-ttu-id="03695-115">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="03695-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03695-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="03695-116">Requirements</span></span>  
 <span data-ttu-id="03695-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03695-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03695-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="03695-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="03695-119">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03695-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03695-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03695-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03695-121">Notes</span><span class="sxs-lookup"><span data-stu-id="03695-121">Remarks</span></span>  
 <span data-ttu-id="03695-122">La signature de nom fort d’un assembly se compose du nom de l’assembly, version, culture et jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="03695-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="03695-123">Si le `StrongNameCompareAssemblies` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="03695-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03695-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03695-124">See Also</span></span>  
 [<span data-ttu-id="03695-125">StrongNameCompareAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="03695-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [<span data-ttu-id="03695-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="03695-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
