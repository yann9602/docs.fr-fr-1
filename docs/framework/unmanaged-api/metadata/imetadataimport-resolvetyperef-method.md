---
title: "IMetaDataImport::ResolveTypeRef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64a783297b27c9d1400670eecb7dfe4cb69c2b96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="0c3ef-102">IMetaDataImport::ResolveTypeRef, méthode</span><span class="sxs-lookup"><span data-stu-id="0c3ef-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="0c3ef-103">Résout un <xref:System.Type> référence représenté par le jeton TypeRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c3ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c3ef-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c3ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c3ef-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="0c3ef-106">[in] Le jeton de métadonnées TypeRef pour retourner les informations de type référencé.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="0c3ef-107">[in] IID de l’interface à retourner dans `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="0c3ef-108">En règle générale, il correspond à IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="0c3ef-109">[out] Interface avec l’étendue du module dans lequel le type référencé est défini.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0c3ef-110">[out] Pointeur vers un jeton TypeDef qui représente le type référencé.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c3ef-111">Notes</span><span class="sxs-lookup"><span data-stu-id="0c3ef-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c3ef-112">N’utilisez pas cette méthode si plusieurs domaines d’application sont chargés.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="0c3ef-113">La méthode ne respecte pas les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="0c3ef-114">Si plusieurs versions d’un assembly sont chargées et qu’ils contiennent le même type avec le même espace de noms, la méthode retourne l’étendue du module du premier type qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="0c3ef-115">Le `ResolveTypeRef` méthode recherche la définition de type dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="0c3ef-116">Si la définition de type est trouvée, `ResolveTypeRef` retourne une interface pour cette portée de module ainsi que le jeton TypeDef pour le type.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="0c3ef-117">Si la référence de type pour être résolu a une portée de résolution AssemblyRef, la `ResolveTypeRef` méthode recherche une correspondance uniquement dans les portées de métadonnées qui ont déjà été ouverte avec des appels à la [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)méthode ou la [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="0c3ef-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="0c3ef-118">C’est parce que `ResolveTypeRef` ne peut pas déterminer à partir d’uniquement l’étendue AssemblyRef où sur le disque ou dans le global assembly cache est stocké l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0c3ef-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c3ef-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0c3ef-119">Requirements</span></span>  
 <span data-ttu-id="0c3ef-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c3ef-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c3ef-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c3ef-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c3ef-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c3ef-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c3ef-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c3ef-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3ef-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c3ef-124">See Also</span></span>  
 [<span data-ttu-id="0c3ef-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="0c3ef-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0c3ef-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="0c3ef-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
