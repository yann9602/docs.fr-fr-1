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
ms.openlocfilehash: 90fcf5ca8306c4e91ff6b96bac36ad2639d81d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="179ab-102">ICLRMetaHost::GetVersionFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="179ab-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="179ab-103">Obtient d’origine .NET Framework version de compilation d’un assembly (stockée dans les métadonnées), étant donnée son chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="179ab-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="179ab-104">Cette méthode remplace la [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="179ab-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="179ab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="179ab-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="179ab-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="179ab-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="179ab-107">[in] Le chemin d’accès de fichier d’assembly complet.</span><span class="sxs-lookup"><span data-stu-id="179ab-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="179ab-108">[out] La version de compilation .NET Framework stockée dans les métadonnées, au format « v*A*. *B*[. *X*] ».</span><span class="sxs-lookup"><span data-stu-id="179ab-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="179ab-109">*A*, *B*, et *X* sont des nombres décimaux qui correspondent à la version principale, la version secondaire et le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="179ab-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="179ab-110">La longueur de cette chaîne est limitée à MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="179ab-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="179ab-111">Cette sortie correspond au nom de répertoire pour la version de .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="179ab-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="179ab-112">Exemples de valeurs sont « v1.0.3705 », « v1.1.4322 », « v2.0.50727 » et « v4.0. *X*», où *X* varie selon le numéro de build installé.</span><span class="sxs-lookup"><span data-stu-id="179ab-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="179ab-113">Notez que le préfixe « v » est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="179ab-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="179ab-114">[dans, out] La taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="179ab-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="179ab-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="179ab-115">Return Value</span></span>  
 <span data-ttu-id="179ab-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="179ab-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="179ab-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="179ab-117">HRESULT</span></span>|<span data-ttu-id="179ab-118">Description</span><span class="sxs-lookup"><span data-stu-id="179ab-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="179ab-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="179ab-119">S_OK</span></span>|<span data-ttu-id="179ab-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="179ab-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="179ab-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="179ab-121">E_POINTER</span></span>|<span data-ttu-id="179ab-122">`pwzbuffer` ou `pcchBuffer` est null.</span><span class="sxs-lookup"><span data-stu-id="179ab-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="179ab-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="179ab-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="179ab-124">La mémoire tampon est trop petite.</span><span class="sxs-lookup"><span data-stu-id="179ab-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="179ab-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="179ab-125">Requirements</span></span>  
 <span data-ttu-id="179ab-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="179ab-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="179ab-127">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="179ab-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="179ab-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="179ab-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="179ab-129">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="179ab-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179ab-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="179ab-130">See Also</span></span>  
 [<span data-ttu-id="179ab-131">ICLRMetaHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="179ab-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="179ab-132">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="179ab-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
