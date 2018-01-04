---
title: "StackOverflowType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowType
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowType
helpviewer_keywords: StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a04db61a16aeae24476fb0b191a3d2dc89743dee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="597cd-102">StackOverflowType, énumération</span><span class="sxs-lookup"><span data-stu-id="597cd-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="597cd-103">Contient des valeurs qui indiquent la cause sous-jacente d’un événement de dépassement de capacité de pile.</span><span class="sxs-lookup"><span data-stu-id="597cd-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="597cd-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="597cd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="597cd-105">Members</span></span>  
  
|<span data-ttu-id="597cd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="597cd-106">Member</span></span>|<span data-ttu-id="597cd-107">Description</span><span class="sxs-lookup"><span data-stu-id="597cd-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="597cd-108">Le dépassement de capacité de pile a été provoquée par le moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="597cd-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="597cd-109">Le dépassement de capacité de pile a été provoquée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="597cd-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="597cd-110">Le dépassement de capacité de pile a été provoquée par le code non managé.</span><span class="sxs-lookup"><span data-stu-id="597cd-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="597cd-111">Notes</span><span class="sxs-lookup"><span data-stu-id="597cd-111">Remarks</span></span>  
 <span data-ttu-id="597cd-112">Ces informations sont passées à l’hôte via un appel à la [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="597cd-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="597cd-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="597cd-113">Requirements</span></span>  
 <span data-ttu-id="597cd-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="597cd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="597cd-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="597cd-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="597cd-116">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="597cd-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="597cd-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="597cd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597cd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="597cd-118">See Also</span></span>  
 [<span data-ttu-id="597cd-119">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="597cd-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
