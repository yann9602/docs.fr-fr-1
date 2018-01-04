---
title: "IMetaDataDispenserEx::GetOption, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fd59fa20e95de8486eaa7f18a63333459361ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="48068-102">IMetaDataDispenserEx::GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="48068-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="48068-103">Obtient la valeur de l’option spécifiée pour la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="48068-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="48068-104">L’option contrôle la gestion des appels à la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="48068-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48068-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48068-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48068-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48068-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="48068-107">[in] Pointeur vers un GUID qui spécifie l’option à récupérer.</span><span class="sxs-lookup"><span data-stu-id="48068-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="48068-108">Consultez la section Notes pour obtenir la liste des GUID pris en charge.</span><span class="sxs-lookup"><span data-stu-id="48068-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="48068-109">[out] La valeur de l’option retournée.</span><span class="sxs-lookup"><span data-stu-id="48068-109">[out] The value of the returned option.</span></span> <span data-ttu-id="48068-110">Le type de cette valeur sera une variante de type de l’option spécifiée.</span><span class="sxs-lookup"><span data-stu-id="48068-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48068-111">Notes</span><span class="sxs-lookup"><span data-stu-id="48068-111">Remarks</span></span>  
 <span data-ttu-id="48068-112">La liste suivante répertorie les GUID qui sont pris en charge pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="48068-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="48068-113">Pour obtenir une description, consultez le [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="48068-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="48068-114">Si `optionId` est pas dans cette liste, cette méthode retourne les HRESULT `E_INVALIDARG`, indiquant un paramètre incorrect.</span><span class="sxs-lookup"><span data-stu-id="48068-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="48068-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="48068-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="48068-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="48068-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="48068-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="48068-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="48068-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="48068-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="48068-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="48068-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="48068-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="48068-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="48068-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="48068-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48068-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="48068-122">Requirements</span></span>  
 <span data-ttu-id="48068-123">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48068-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48068-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48068-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48068-125">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48068-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48068-126">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48068-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48068-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48068-127">See Also</span></span>  
 [<span data-ttu-id="48068-128">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="48068-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="48068-129">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="48068-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
