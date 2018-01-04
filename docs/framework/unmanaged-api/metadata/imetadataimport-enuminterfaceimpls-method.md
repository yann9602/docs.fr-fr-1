---
title: "IMetaDataImport::EnumInterfaceImpls, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumInterfaceImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646d65ff81795ce0558651db9c3fe1bc7205ae08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="79721-102">IMetaDataImport::EnumInterfaceImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="79721-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="79721-103">Énumère les jetons MethodDef représentant des implémentations d'interface.</span><span class="sxs-lookup"><span data-stu-id="79721-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79721-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79721-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79721-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79721-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="79721-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="79721-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="79721-107">[in] Le jeton du TypeDef dont les jetons MethodDef représentant des implémentations d’interface doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="79721-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="79721-108">[out] Tableau utilisé pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="79721-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="79721-109">[in] Taille maximale du tableau `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="79721-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="79721-110">[out] Le nombre réel de jetons retournés dans `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="79721-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79721-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79721-111">Return Value</span></span>  
  
|<span data-ttu-id="79721-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79721-112">HRESULT</span></span>|<span data-ttu-id="79721-113">Description</span><span class="sxs-lookup"><span data-stu-id="79721-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="79721-114">`EnumInterfaceImpls`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="79721-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="79721-115">Il n’existe pas de jetons MethodDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="79721-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="79721-116">Dans ce cas, `pcImpls` est définie sur zéro.</span><span class="sxs-lookup"><span data-stu-id="79721-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79721-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79721-117">Requirements</span></span>  
 <span data-ttu-id="79721-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79721-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79721-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="79721-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79721-120">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79721-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79721-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79721-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79721-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79721-122">See Also</span></span>  
 [<span data-ttu-id="79721-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="79721-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="79721-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="79721-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
