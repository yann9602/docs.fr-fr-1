---
title: GetCORSystemDirectory, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02b695ac7f75dd38da8cd06e1444af4ae425ebd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="1b763-102">GetCORSystemDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="1b763-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="1b763-103">Retourne le répertoire d’installation du common language runtime (CLR) qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1b763-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="1b763-104">Le répertoire d’installation est qualifié complet, par exemple, « c:\windows\microsoft.net\framework\v1.0.3705 ».</span><span class="sxs-lookup"><span data-stu-id="1b763-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="1b763-105">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="1b763-105">This function is deprecated.</span></span> <span data-ttu-id="1b763-106">Il est remplacé par le [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) méthode fourni dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b763-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b763-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b763-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b763-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b763-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="1b763-109">[out] Une mémoire tampon dans laquelle le runtime retourne une chaîne qui contient le nom qualifié complet du répertoire d’installation pour le runtime chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1b763-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="1b763-110">Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire approprié pour la version la plus récente du runtime installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1b763-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="1b763-111">[in] La taille, en octets, de `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="1b763-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="1b763-112">[out] Le nombre de caractères retournés dans `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="1b763-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b763-113">Notes</span><span class="sxs-lookup"><span data-stu-id="1b763-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1b763-114">N’utilisez pas cette fonction dans les processus qui exécutent la version 4 du CLR.</span><span class="sxs-lookup"><span data-stu-id="1b763-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="1b763-115">Si une version antérieure du CLR est installée sur l’ordinateur, cette fonction retourne le répertoire d’installation pour cette version.</span><span class="sxs-lookup"><span data-stu-id="1b763-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b763-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b763-116">Requirements</span></span>  
 <span data-ttu-id="1b763-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b763-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b763-118">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b763-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b763-119">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b763-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b763-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b763-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b763-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b763-121">See Also</span></span>  
 [<span data-ttu-id="1b763-122">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="1b763-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
