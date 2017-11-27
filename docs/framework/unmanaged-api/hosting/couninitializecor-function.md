---
title: CoUninitializeCor, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeCor
helpviewer_keywords: CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57740ed8f20891b240bca5e9e19591484022b8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="054bb-102">CoUninitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="054bb-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="054bb-103">`CoUninitializeCor` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="054bb-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="054bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="054bb-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="054bb-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="054bb-105">Remarks</span></span>  
 <span data-ttu-id="054bb-106">Le common language runtime ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="054bb-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="054bb-107">Pour supprimer complètement le runtime d’un processus en cours d’exécution, vous devez arrêter ce processus.</span><span class="sxs-lookup"><span data-stu-id="054bb-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054bb-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="054bb-108">See Also</span></span>  
 [<span data-ttu-id="054bb-109">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="054bb-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
