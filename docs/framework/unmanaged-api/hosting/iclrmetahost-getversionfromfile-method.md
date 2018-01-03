---
title: "ICLRMetaHost::GetVersionFromFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetVersionFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e6cd1c83cc369e06099c72a6012eb448d6d37a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="f7454-102">ICLRMetaHost::GetVersionFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="f7454-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="f7454-103">Obtient d’origine .NET Framework version de compilation d’un assembly (stockée dans les métadonnées), étant donnée son chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="f7454-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="f7454-104">Cette méthode remplace la [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="f7454-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7454-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7454-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7454-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7454-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f7454-107">[in] Le chemin d’accès de fichier d’assembly complet.</span><span class="sxs-lookup"><span data-stu-id="f7454-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="f7454-108">[out] La version de compilation .NET Framework stockée dans les métadonnées, au format « v*A*. *B*[. *X*] ».</span><span class="sxs-lookup"><span data-stu-id="f7454-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="f7454-109">*A*, *B*, et *X* sont des nombres décimaux qui correspondent à la version principale, la version secondaire et le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="f7454-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="f7454-110">La longueur de cette chaîne est limitée à MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="f7454-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7454-111">Cette sortie correspond au nom de répertoire pour la version de .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="f7454-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="f7454-112">Exemples de valeurs sont « v1.0.3705 », « v1.1.4322 », « v2.0.50727 » et « v4.0. *X*», où *X* varie selon le numéro de build installé.</span><span class="sxs-lookup"><span data-stu-id="f7454-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="f7454-113">Notez que le préfixe « v » est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f7454-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="f7454-114">[dans, out] La taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f7454-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7454-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7454-115">Return Value</span></span>  
 <span data-ttu-id="f7454-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f7454-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f7454-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7454-117">HRESULT</span></span>|<span data-ttu-id="f7454-118">Description</span><span class="sxs-lookup"><span data-stu-id="f7454-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7454-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7454-119">S_OK</span></span>|<span data-ttu-id="f7454-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="f7454-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="f7454-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f7454-121">E_POINTER</span></span>|<span data-ttu-id="f7454-122">`pwzbuffer` ou `pcchBuffer` est null.</span><span class="sxs-lookup"><span data-stu-id="f7454-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="f7454-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="f7454-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="f7454-124">La mémoire tampon est trop petite.</span><span class="sxs-lookup"><span data-stu-id="f7454-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7454-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7454-125">Requirements</span></span>  
 <span data-ttu-id="f7454-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7454-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7454-127">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f7454-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f7454-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7454-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7454-129">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7454-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7454-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7454-130">See Also</span></span>  
 [<span data-ttu-id="f7454-131">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="f7454-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="f7454-132">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="f7454-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
