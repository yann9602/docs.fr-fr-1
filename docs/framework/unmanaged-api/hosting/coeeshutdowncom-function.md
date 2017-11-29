---
title: CoEEShutDownCOM, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d6d9e3d650f65ef084c63104980bca0ac77f1bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="5b11f-102">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="5b11f-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="5b11f-103">Force le common language runtime (CLR) pour libérer tous les pointeurs d’interface qu’il conserve dans callable wrappers RCW (runtime).</span><span class="sxs-lookup"><span data-stu-id="5b11f-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="5b11f-104">Cela a pour effet de libérer tous les caches RCW.</span><span class="sxs-lookup"><span data-stu-id="5b11f-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="5b11f-105">Cette fonction globale est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b11f-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="5b11f-106">Au lieu de cela, utilisez le point d’entrée pour une exécution spécifique.</span><span class="sxs-lookup"><span data-stu-id="5b11f-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b11f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b11f-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5b11f-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="5b11f-108">Remarks</span></span>  
 <span data-ttu-id="5b11f-109">Le `CoEEShutDownCOM` fonction diffuse en premier tous les wrappers RCW dans tous les contextes et dans tous les caches, puis supprime toute notification destructions existant dans le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="5b11f-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="5b11f-110">Aucun déchargement de DLL se produit.</span><span class="sxs-lookup"><span data-stu-id="5b11f-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5b11f-111">Cette fonction affecte tous les runtimes chargés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5b11f-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="5b11f-112">Compter les [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], appelez le point d’entrée pour cette fonction sur le runtime spécifique que vous souhaitez affecter.</span><span class="sxs-lookup"><span data-stu-id="5b11f-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="5b11f-113">Pour obtenir le point d’entrée, appelez le [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) (méthode) et spécifiez « CoEEShutDownCOM ».</span><span class="sxs-lookup"><span data-stu-id="5b11f-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b11f-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5b11f-114">Requirements</span></span>  
 <span data-ttu-id="5b11f-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b11f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b11f-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5b11f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b11f-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b11f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b11f-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b11f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b11f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b11f-119">See Also</span></span>  
 [<span data-ttu-id="5b11f-120">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="5b11f-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
