---
title: CorLaunchApplication, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6246ab600438e2237dcbe531d9d7641c0897d81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="6394a-102">CorLaunchApplication, fonction</span><span class="sxs-lookup"><span data-stu-id="6394a-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="6394a-103">Démarre l’application sur le chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="6394a-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="6394a-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6394a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6394a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6394a-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6394a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6394a-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="6394a-107">[in] Une valeur de la [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) énumération qui spécifie le type d’hôte qui lance l’application.</span><span class="sxs-lookup"><span data-stu-id="6394a-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="6394a-108">[in] Le nom complet de l’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="6394a-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="6394a-109">[in] Le nombre de chemins d’accès de manifestes de l’application.</span><span class="sxs-lookup"><span data-stu-id="6394a-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="6394a-110">[in] Un tableau de chaînes, dont chacun spécifie un chemin d’accès à un manifeste d’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="6394a-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="6394a-111">[in] Nombre d’éléments de données d’activation pour l’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="6394a-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="6394a-112">[in] Un tableau de chaînes, chacune d’elles est un élément de données d’activation pour l’application qui est lancée.</span><span class="sxs-lookup"><span data-stu-id="6394a-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="6394a-113">[out] Pointeur vers les informations sur le processus dans lequel l’application a été chargée.</span><span class="sxs-lookup"><span data-stu-id="6394a-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6394a-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6394a-114">Requirements</span></span>  
 <span data-ttu-id="6394a-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6394a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6394a-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6394a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6394a-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6394a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6394a-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6394a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6394a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6394a-119">See Also</span></span>  
 [<span data-ttu-id="6394a-120">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="6394a-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
