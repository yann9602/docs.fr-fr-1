---
title: GetHistoryFileDirectory, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHistoryFileDirectory
api_location: fusion.dll
api_type: DLLExport
f1_keywords: GetHistoryFileDirectory
helpviewer_keywords: GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="52419-102">GetHistoryFileDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="52419-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="52419-103">Récupère le chemin d’accès du répertoire de l’historique de l’application.</span><span class="sxs-lookup"><span data-stu-id="52419-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52419-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52419-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52419-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52419-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="52419-106">[out] Une mémoire tampon pour stocker le chemin d’accès au répertoire de l’historique de l’application.</span><span class="sxs-lookup"><span data-stu-id="52419-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="52419-107">[dans, out] La longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="52419-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52419-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="52419-108">Return Value</span></span>  
 <span data-ttu-id="52419-109">Cette méthode retourne des codes d’erreur COM standard, tel que défini dans le fichier WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="52419-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="52419-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="52419-110">Return code</span></span>|<span data-ttu-id="52419-111">Description</span><span class="sxs-lookup"><span data-stu-id="52419-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="52419-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="52419-112">S_OK</span></span>|<span data-ttu-id="52419-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="52419-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="52419-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="52419-114">E_INVALIDARG</span></span>|<span data-ttu-id="52419-115">`wzDir`ou `pdwSize` est null, ou la version de chaîne est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="52419-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52419-116">Notes</span><span class="sxs-lookup"><span data-stu-id="52419-116">Remarks</span></span>  
 <span data-ttu-id="52419-117">Opération réussie, le `pdwSize` argument est défini à la longueur de la chaîne de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="52419-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52419-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="52419-118">Requirements</span></span>  
 <span data-ttu-id="52419-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52419-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52419-120">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="52419-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="52419-121">**Bibliothèque :** Fusion.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="52419-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="52419-122">Utilisez le fichier Fusion.dll plutôt que Mscorwks.dll pour garantir que vous ciblez la version appropriée du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52419-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="52419-123">**Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52419-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52419-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52419-124">See Also</span></span>  
 [<span data-ttu-id="52419-125">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="52419-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="52419-126">NukeDownloadedCache, fonction</span><span class="sxs-lookup"><span data-stu-id="52419-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="52419-127">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="52419-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
