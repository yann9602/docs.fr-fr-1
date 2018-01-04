---
title: "IMetaDataImport::EnumEvents, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumEvents
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed783cf80fb068656855c2c06ab814f665f1cede
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="0e122-102">IMetaDataImport::EnumEvents, méthode</span><span class="sxs-lookup"><span data-stu-id="0e122-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="0e122-103">Énumère les jetons de définition d'événements pour le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e122-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e122-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e122-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e122-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e122-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0e122-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0e122-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="0e122-107">[in] Le jeton TypeDef dont les définitions d’événement doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="0e122-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="0e122-108">[out] Tableau d’événements retournés.</span><span class="sxs-lookup"><span data-stu-id="0e122-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0e122-109">[in] Taille maximale du tableau `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="0e122-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="0e122-110">[out] Le nombre réel d’événements retournés dans `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="0e122-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e122-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0e122-111">Return Value</span></span>  
  
|<span data-ttu-id="0e122-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e122-112">HRESULT</span></span>|<span data-ttu-id="0e122-113">Description</span><span class="sxs-lookup"><span data-stu-id="0e122-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0e122-114">`EnumEvents`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0e122-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0e122-115">Il n’existe pas d’événements à énumérer.</span><span class="sxs-lookup"><span data-stu-id="0e122-115">There are no events to enumerate.</span></span> <span data-ttu-id="0e122-116">Dans ce cas, `pcEvents` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="0e122-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e122-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e122-117">Requirements</span></span>  
 <span data-ttu-id="0e122-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e122-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e122-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e122-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e122-120">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e122-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e122-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e122-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e122-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e122-122">See Also</span></span>  
 [<span data-ttu-id="0e122-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="0e122-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0e122-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="0e122-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
