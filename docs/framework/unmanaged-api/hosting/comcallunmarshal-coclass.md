---
title: Coclasse ComCallUnmarshal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ComCallUnmarshal Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: ComCallUnmarshal
helpviewer_keywords: ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2760fc84466c85e022421bcc17dcee6444ec859a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="474ca-102">Coclasse ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="474ca-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="474ca-103">Fournit des interfaces pour gérer le marshaling de pointeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="474ca-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="474ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="474ca-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="474ca-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="474ca-105">Interfaces</span></span>  
  
|<span data-ttu-id="474ca-106">Interface</span><span class="sxs-lookup"><span data-stu-id="474ca-106">Interface</span></span>|<span data-ttu-id="474ca-107">Description</span><span class="sxs-lookup"><span data-stu-id="474ca-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="474ca-108">Fournit des méthodes de création, de l’initialisation et de gérer un proxy dans un processus client.</span><span class="sxs-lookup"><span data-stu-id="474ca-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="474ca-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="474ca-109">Requirements</span></span>  
 <span data-ttu-id="474ca-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="474ca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="474ca-111">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="474ca-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="474ca-112">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="474ca-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="474ca-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="474ca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474ca-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="474ca-114">See Also</span></span>  
 [<span data-ttu-id="474ca-115">Coclasses d’hébergement</span><span class="sxs-lookup"><span data-stu-id="474ca-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
