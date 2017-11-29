---
title: CorpubPublish (coclasse)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c1565c9321e64536139e02b239fbeb4247a58a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="58365-102">CorpubPublish (coclasse)</span><span class="sxs-lookup"><span data-stu-id="58365-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="58365-103">Fournit les interfaces pour la publication d'informations sur les domaines d'application et les processus.</span><span class="sxs-lookup"><span data-stu-id="58365-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58365-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58365-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="58365-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="58365-105">Interfaces</span></span>  
  
|<span data-ttu-id="58365-106">Interface</span><span class="sxs-lookup"><span data-stu-id="58365-106">Interface</span></span>|<span data-ttu-id="58365-107">Description</span><span class="sxs-lookup"><span data-stu-id="58365-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="58365-108">ICorPublish (Interface)</span><span class="sxs-lookup"><span data-stu-id="58365-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="58365-109">Fournit des méthodes pour la publication des informations sur les processus et les domaines d’application dans ces processus.</span><span class="sxs-lookup"><span data-stu-id="58365-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="58365-110">ICorPublishAppDomain (Interface)</span><span class="sxs-lookup"><span data-stu-id="58365-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="58365-111">Représente et fournit des informations sur un domaine d’application dans un processus.</span><span class="sxs-lookup"><span data-stu-id="58365-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="58365-112">ICorPublishAppDomainEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="58365-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="58365-113">Fournit des méthodes qui parcourent une collection de domaines d’application qui existent actuellement dans un processus.</span><span class="sxs-lookup"><span data-stu-id="58365-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="58365-114">ICorPublishProcess (Interface)</span><span class="sxs-lookup"><span data-stu-id="58365-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="58365-115">Représente un processus qui s’exécute sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="58365-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="58365-116">ICorPublishProcessEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="58365-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="58365-117">Fournit des méthodes qui parcourent une collection de processus qui s’exécutent sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="58365-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58365-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="58365-118">Remarks</span></span>  
 <span data-ttu-id="58365-119">Un scénario classique de publication implique un développeur qui souhaite déboguer du code managé qui s’exécute sur un ordinateur dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="58365-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="58365-120">L’environnement d’hébergement peut exécuter plusieurs domaines d’application dans un processus.</span><span class="sxs-lookup"><span data-stu-id="58365-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="58365-121">Le développeur souhaite utiliser une interface utilisateur graphique ou autres moyens pour répertorier tous les processus qui sont exécutent sur l’ordinateur et choisir un processus spécifique.</span><span class="sxs-lookup"><span data-stu-id="58365-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="58365-122">La liste doit inclure tous les domaines d’application dans les processus qui sont en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="58365-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="58365-123">Le développeur peut ensuite identifier le domaine d’application spécifique et joindre un débogueur à ce domaine.</span><span class="sxs-lookup"><span data-stu-id="58365-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58365-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="58365-124">Requirements</span></span>  
 <span data-ttu-id="58365-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58365-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58365-126">**En-tête :** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="58365-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="58365-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58365-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58365-128">**Versions du .NET framework :**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58365-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58365-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58365-129">See Also</span></span>  
 [<span data-ttu-id="58365-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="58365-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
