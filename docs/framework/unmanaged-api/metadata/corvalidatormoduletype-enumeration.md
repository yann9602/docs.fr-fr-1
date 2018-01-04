---
title: "CorValidatorModuleType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorValidatorModuleType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorValidatorModuleType
helpviewer_keywords: CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3367f6928b5d7378b2686185ee3e03d0279cc11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="af863-102">CorValidatorModuleType, énumération</span><span class="sxs-lookup"><span data-stu-id="af863-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="af863-103">Spécifie le type d’un module.</span><span class="sxs-lookup"><span data-stu-id="af863-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af863-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af863-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="af863-105">Membres</span><span class="sxs-lookup"><span data-stu-id="af863-105">Members</span></span>  
  
|<span data-ttu-id="af863-106">Membre</span><span class="sxs-lookup"><span data-stu-id="af863-106">Member</span></span>|<span data-ttu-id="af863-107">Description</span><span class="sxs-lookup"><span data-stu-id="af863-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="af863-108">Le module est un type non valide.</span><span class="sxs-lookup"><span data-stu-id="af863-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="af863-109">La valeur minimale de la `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="af863-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="af863-110">Le module est un fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="af863-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="af863-111">Le module est un fichier .obj.</span><span class="sxs-lookup"><span data-stu-id="af863-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="af863-112">Le module est une session du débogueur de modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="af863-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="af863-113">Le module est celle qui a été généré de façon incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="af863-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="af863-114">La valeur maximale de la `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="af863-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af863-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="af863-115">Requirements</span></span>  
 <span data-ttu-id="af863-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af863-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af863-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af863-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af863-118">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af863-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af863-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af863-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af863-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af863-120">See Also</span></span>  
 [<span data-ttu-id="af863-121">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="af863-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
