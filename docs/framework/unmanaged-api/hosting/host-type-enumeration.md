---
title: "HOST_TYPE, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: HOST_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: HOST_TYPE
helpviewer_keywords: HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8c910dd06109a8a69f29517812737d4b4dcef21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="63a28-102">HOST_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="63a28-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="63a28-103">Contient des valeurs qui spécifient le type d’hôte qui lance une application.</span><span class="sxs-lookup"><span data-stu-id="63a28-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63a28-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="63a28-105">Membres</span><span class="sxs-lookup"><span data-stu-id="63a28-105">Members</span></span>  
  
|<span data-ttu-id="63a28-106">Membre</span><span class="sxs-lookup"><span data-stu-id="63a28-106">Member</span></span>|<span data-ttu-id="63a28-107">Description</span><span class="sxs-lookup"><span data-stu-id="63a28-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="63a28-108">Lancez l’application à partir d’AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="63a28-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="63a28-109">Utilisez cette valeur pour les applications de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="63a28-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="63a28-110">Lancer l’application directement.</span><span class="sxs-lookup"><span data-stu-id="63a28-110">Launch the application directly.</span></span> <span data-ttu-id="63a28-111">Autrement dit, lancez l’application à partir de son propre fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="63a28-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="63a28-112">Utilisez cette valeur pour les applications de confiance.</span><span class="sxs-lookup"><span data-stu-id="63a28-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="63a28-113">Identique à HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="63a28-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63a28-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="63a28-114">Requirements</span></span>  
 <span data-ttu-id="63a28-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63a28-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63a28-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63a28-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63a28-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63a28-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63a28-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63a28-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a28-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63a28-119">See Also</span></span>  
 [<span data-ttu-id="63a28-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="63a28-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
