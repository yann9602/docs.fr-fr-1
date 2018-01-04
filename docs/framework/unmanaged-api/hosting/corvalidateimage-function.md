---
title: _CorValidateImage, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorValidateImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorValidateImage
helpviewer_keywords: _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03deb62a84a1e9c6cee898fe0023c34b8c538ece
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="f2509-102">_CorValidateImage, fonction</span><span class="sxs-lookup"><span data-stu-id="f2509-102">_CorValidateImage Function</span></span>
<span data-ttu-id="f2509-103">Valide les images de modules managés et notifie le chargeur du système d’exploitation après avoir été chargés.</span><span class="sxs-lookup"><span data-stu-id="f2509-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2509-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2509-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2509-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2509-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="f2509-106">[in] Un pointeur vers l’emplacement de départ de l’image à valider en tant que le code managé.</span><span class="sxs-lookup"><span data-stu-id="f2509-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="f2509-107">L’image doit être déjà chargée en mémoire.</span><span class="sxs-lookup"><span data-stu-id="f2509-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="f2509-108">[in] Le nom de fichier de l’image.</span><span class="sxs-lookup"><span data-stu-id="f2509-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2509-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f2509-109">Return Value</span></span>  
 <span data-ttu-id="f2509-110">Cette fonction retourne les valeurs standard `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, et `E_FAIL`, ainsi que les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="f2509-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="f2509-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f2509-111">Return value</span></span>|<span data-ttu-id="f2509-112">Description</span><span class="sxs-lookup"><span data-stu-id="f2509-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="f2509-113">L’image n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="f2509-113">The image is invalid.</span></span> <span data-ttu-id="f2509-114">Cette valeur possède le HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="f2509-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="f2509-115">L’image est valide.</span><span class="sxs-lookup"><span data-stu-id="f2509-115">The image is valid.</span></span> <span data-ttu-id="f2509-116">Cette valeur possède le HRESULT 0x00000000L.</span><span class="sxs-lookup"><span data-stu-id="f2509-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2509-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f2509-117">Remarks</span></span>  
 <span data-ttu-id="f2509-118">Dans Windows XP et versions ultérieures, le chargeur du système d’exploitation recherche des modules managés en examinant le bit du répertoire du descripteur COM dans l’en-tête common object file format (COFF).</span><span class="sxs-lookup"><span data-stu-id="f2509-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="f2509-119">Un bit défini indique un module managé.</span><span class="sxs-lookup"><span data-stu-id="f2509-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="f2509-120">Si le chargeur détecte un module managé, il charge MsCorEE.dll et appelle `_CorValidateImage`, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2509-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="f2509-121">Confirme que l’image est un module managé valid.</span><span class="sxs-lookup"><span data-stu-id="f2509-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="f2509-122">Modifie le point d’entrée dans l’image à un point d’entrée dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f2509-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="f2509-123">Pour les versions 64 bits de Windows, modifie l’image en mémoire en la transformant du format PE32 au format PE32 +.</span><span class="sxs-lookup"><span data-stu-id="f2509-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="f2509-124">Retourne au chargeur lorsque les images de modules managés sont chargées.</span><span class="sxs-lookup"><span data-stu-id="f2509-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="f2509-125">Pour les images exécutables, le chargeur du système d’exploitation appelle ensuite la [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) (fonction), quel que soit le point d’entrée spécifié dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="f2509-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="f2509-126">Pour les images d’assembly DLL, le chargeur appelle la [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="f2509-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="f2509-127">`_CorExeMain`ou `_CorDllMain` effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2509-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="f2509-128">Initialise le CLR.</span><span class="sxs-lookup"><span data-stu-id="f2509-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="f2509-129">Recherche le point d’entrée managé à partir de l’en-tête du CLR de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f2509-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="f2509-130">Commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f2509-130">Begins execution.</span></span>  
  
 <span data-ttu-id="f2509-131">Les appels de chargeur du [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) fonctionner lorsque gérés images sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="f2509-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="f2509-132">Toutefois, cette fonction n’effectue pas d’action ; elle renvoie simplement.</span><span class="sxs-lookup"><span data-stu-id="f2509-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2509-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2509-133">Requirements</span></span>  
 <span data-ttu-id="f2509-134">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2509-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2509-135">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2509-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2509-136">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2509-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2509-137">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2509-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2509-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2509-138">See Also</span></span>  
 [<span data-ttu-id="f2509-139">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="f2509-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
