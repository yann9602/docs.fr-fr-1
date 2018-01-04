---
title: "IMetaDataEmit::DefineTypeRefByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46b9fe83a5beb031d4ac21deb903060e2f788e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="d3e8a-102">IMetaDataEmit::DefineTypeRefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="d3e8a-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="d3e8a-103">Obtient le jeton de métadonnées pour un type qui est défini dans l’étendue spécifiée, qui est en dehors de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e8a-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3e8a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3e8a-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="d3e8a-106">[in] Le jeton spécifiant la portée de résolution.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="d3e8a-107">Les types de jetons suivants sont valides :</span><span class="sxs-lookup"><span data-stu-id="d3e8a-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="d3e8a-108">`mdModuleRef`, si le type est défini dans le même assembly dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="d3e8a-109">`mdAssemblyRef`, si le type est défini dans un assembly autre que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="d3e8a-110">`mdTypeRef`, si le type est un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="d3e8a-111">`mdModule`, si le type est défini dans le même module que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="d3e8a-112">NULL, si le type est défini globalement.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="d3e8a-113">[in] Le nom du type cible au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="d3e8a-114">[out] Un pointeur vers le `mdTypeRef` jeton qui est assigné au type.</span><span class="sxs-lookup"><span data-stu-id="d3e8a-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3e8a-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d3e8a-115">Requirements</span></span>  
 <span data-ttu-id="d3e8a-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3e8a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3e8a-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3e8a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3e8a-118">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3e8a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3e8a-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e8a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e8a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e8a-120">See Also</span></span>  
 [<span data-ttu-id="d3e8a-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d3e8a-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d3e8a-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d3e8a-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
