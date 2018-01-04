---
title: LoadStringRC, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fd42a576e1315ea029f98b94d8dc84d2b92b5e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="loadstringrc-function"></a><span data-ttu-id="ec2bd-102">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="ec2bd-102">LoadStringRC Function</span></span>
<span data-ttu-id="ec2bd-103">Traduit une valeur HRESULT dans un message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="ec2bd-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec2bd-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec2bd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec2bd-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec2bd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec2bd-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="ec2bd-107">[in] Une valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="ec2bd-108">[out] Une mémoire tampon qui contient le message d’erreur en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="ec2bd-109">[in] La taille de la mémoire tampon de message.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="ec2bd-110">[in] Ignoré.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec2bd-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ec2bd-111">Return Value</span></span>  
 <span data-ttu-id="ec2bd-112">Cette méthode retourne des codes d’erreur de modèle COM (Component Object) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ec2bd-113">Code de retour</span><span class="sxs-lookup"><span data-stu-id="ec2bd-113">Return code</span></span>|<span data-ttu-id="ec2bd-114">Description</span><span class="sxs-lookup"><span data-stu-id="ec2bd-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ec2bd-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec2bd-115">S_OK</span></span>|<span data-ttu-id="ec2bd-116">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="ec2bd-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ec2bd-117">E_INVALIDARG</span></span>|<span data-ttu-id="ec2bd-118">`szBuffer`a la valeur null ou `iMax` est zéro (0).</span><span class="sxs-lookup"><span data-stu-id="ec2bd-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec2bd-119">Notes</span><span class="sxs-lookup"><span data-stu-id="ec2bd-119">Remarks</span></span>  
 <span data-ttu-id="ec2bd-120">Si la méthode ne se termine pas correctement, `szBuffer` contient une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec2bd-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec2bd-121">Requirements</span></span>  
 <span data-ttu-id="ec2bd-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec2bd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec2bd-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec2bd-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec2bd-124">**Bibliothèque :** MSCorEE.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="ec2bd-125">Utilisez MSCorEE.dll plutôt que Mscorwks.dll pour garantir que vous ciblez la version appropriée du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec2bd-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ec2bd-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec2bd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2bd-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec2bd-127">See Also</span></span>  
 [<span data-ttu-id="ec2bd-128">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="ec2bd-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="ec2bd-129">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="ec2bd-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
