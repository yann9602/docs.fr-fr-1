---
title: "RUNTIME_INFO_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 697111efbb4e3f705c881ec677f781b6e3e6959d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="5b9b8-102">RUNTIME_INFO_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="5b9b8-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="5b9b8-103">Contient des valeurs qui indiquent les informations sur le common language runtime (CLR) doivent être retournées.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b9b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b9b8-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5b9b8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5b9b8-105">Members</span></span>  
  
|<span data-ttu-id="5b9b8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5b9b8-106">Member</span></span>|<span data-ttu-id="5b9b8-107">Description</span><span class="sxs-lookup"><span data-stu-id="5b9b8-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="5b9b8-108">Indique que les informations d’annuaire ne doivent pas être incluses.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="5b9b8-109">Indique que les informations de version ne doivent pas être incluses.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="5b9b8-110">Indique qu’une boîte de dialogue d’erreur ne doit pas s’afficher en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="5b9b8-111">Indique que les effets de l’appel de la [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) fonction avec l’indicateur SEM_FAILCRITICALERRORS doit être substituée.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-111">Indicates that the effects of calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="5b9b8-112">Autrement dit, une boîte de dialogue d’installation doit être affichée en cas d’échec, au lieu d’en cours de suppression.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="5b9b8-113">Indique une demande d’informations sur une version compatible AMD-64 de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="5b9b8-114">Indique une demande d’informations sur une version compatible IA-64 de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="5b9b8-115">Indique une demande d’informations sur une version compatible avec x86 du runtime.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="5b9b8-116">Indique que les informations de mise à niveau de version doivent être incluses.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b9b8-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="5b9b8-117">Remarks</span></span>  
 <span data-ttu-id="5b9b8-118">Les indicateurs d’architecture de plateforme suivants peuvent être spécifiés une seule à la fois et ne peut pas être combinées :</span><span class="sxs-lookup"><span data-stu-id="5b9b8-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="5b9b8-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="5b9b8-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="5b9b8-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="5b9b8-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="5b9b8-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="5b9b8-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b9b8-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5b9b8-122">Requirements</span></span>  
 <span data-ttu-id="5b9b8-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b9b8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b9b8-124">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b9b8-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b9b8-125">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b9b8-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b9b8-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b9b8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b9b8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b9b8-127">See Also</span></span>  
 [<span data-ttu-id="5b9b8-128">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5b9b8-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
