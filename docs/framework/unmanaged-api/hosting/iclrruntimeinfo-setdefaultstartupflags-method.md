---
title: "ICLRRuntimeInfo::SetDefaultStartupFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.SetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1732073b9799453bd32447e7a688b0280e66f1ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="31344-102">ICLRRuntimeInfo::SetDefaultStartupFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="31344-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="31344-103">Définit les indicateurs de démarrage et le fichier de configuration d’hôte qui permet de démarrer le runtime.</span><span class="sxs-lookup"><span data-stu-id="31344-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="31344-104">Cette méthode remplace l’utilisation de la `startupFlags` paramètre dans le [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) fonctions.</span><span class="sxs-lookup"><span data-stu-id="31344-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31344-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31344-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31344-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31344-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="31344-107">[in] Les indicateurs de démarrage hôtes à définir.</span><span class="sxs-lookup"><span data-stu-id="31344-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="31344-108">Utilisez les mêmes indicateurs comme avec la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) fonctions.</span><span class="sxs-lookup"><span data-stu-id="31344-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="31344-109">[in] Le chemin du répertoire du fichier de configuration hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="31344-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31344-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31344-110">Return Value</span></span>  
 <span data-ttu-id="31344-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l’échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="31344-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="31344-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31344-112">HRESULT</span></span>|<span data-ttu-id="31344-113">Description</span><span class="sxs-lookup"><span data-stu-id="31344-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31344-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="31344-114">S_OK</span></span>|<span data-ttu-id="31344-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="31344-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31344-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="31344-116">Remarks</span></span>  
 <span data-ttu-id="31344-117">Un hôte multithread doit synchroniser des appels à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="31344-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="31344-118">Sinon, le thread A peut appeler le `SetStartupFlags` méthode une fois que le thread B a terminé un appel à `SetStartupFlags` et avant que le thread B démarre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="31344-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31344-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="31344-119">Requirements</span></span>  
 <span data-ttu-id="31344-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31344-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31344-121">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="31344-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="31344-122">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31344-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31344-123">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31344-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31344-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31344-124">See Also</span></span>  
 [<span data-ttu-id="31344-125">ICLRRuntimeInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="31344-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="31344-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="31344-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="31344-127">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="31344-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
