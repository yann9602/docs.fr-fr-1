---
title: NukeDownloadedCache, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31d7ba7d5f4a9268ea1e04a4c9f09cd17ebfd5bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="08b03-102">NukeDownloadedCache, fonction</span><span class="sxs-lookup"><span data-stu-id="08b03-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="08b03-103">Supprime le cache de téléchargement du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="08b03-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08b03-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="08b03-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="08b03-105">Return Value</span></span>  
 <span data-ttu-id="08b03-106">Cette méthode retourne des codes d’erreur COM standard, tel que défini dans WinError.h.</span><span class="sxs-lookup"><span data-stu-id="08b03-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08b03-107">Notes</span><span class="sxs-lookup"><span data-stu-id="08b03-107">Remarks</span></span>  
 <span data-ttu-id="08b03-108">Le cache de téléchargement CLR est la zone où les assemblys avec nom fort qui sont téléchargés à partir d’une URL sont stockés pour une réutilisation éventuelle.</span><span class="sxs-lookup"><span data-stu-id="08b03-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b03-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08b03-109">Requirements</span></span>  
 <span data-ttu-id="08b03-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08b03-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08b03-111">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="08b03-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="08b03-112">**Bibliothèque :** Fusion.dll et Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="08b03-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="08b03-113">Utilisez le fichier Fusion.dll plutôt que Mscorwks.dll pour garantir que vous ciblez la version appropriée du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08b03-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="08b03-114">**Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08b03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b03-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08b03-115">See Also</span></span>  
 [<span data-ttu-id="08b03-116">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="08b03-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="08b03-117">GetHistoryFileDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="08b03-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="08b03-118">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="08b03-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
