---
title: _CorImageUnloading, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorImageUnloading
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorImageUnloading
helpviewer_keywords: _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90df58e2765cdecf4a1ec22cf5540e5cfa9530a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corimageunloading-function"></a><span data-ttu-id="654ba-102">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="654ba-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="654ba-103">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="654ba-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="654ba-104">Cette fonction n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="654ba-104">This function is not implemented.</span></span> <span data-ttu-id="654ba-105">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="654ba-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654ba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="654ba-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="654ba-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="654ba-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="654ba-108">[in] Pointeur vers l’emplacement de départ de l’image à décharger.</span><span class="sxs-lookup"><span data-stu-id="654ba-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="654ba-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="654ba-109">Requirements</span></span>  
 <span data-ttu-id="654ba-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="654ba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="654ba-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="654ba-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="654ba-112">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="654ba-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="654ba-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="654ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654ba-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="654ba-114">See Also</span></span>  
 [<span data-ttu-id="654ba-115">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="654ba-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
