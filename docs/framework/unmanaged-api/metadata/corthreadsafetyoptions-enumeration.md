---
title: "CorThreadSafetyOptions, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorThreadSafetyOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorThreadSafetyOptions
helpviewer_keywords: CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e017732882841e1cb2b5f00b1c51e22bba11ae73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="6de4b-102">CorThreadSafetyOptions, énumération</span><span class="sxs-lookup"><span data-stu-id="6de4b-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="6de4b-103">Spécifie des indicateurs permettant de sélectionner des options pour la sécurité des threads.</span><span class="sxs-lookup"><span data-stu-id="6de4b-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de4b-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="6de4b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6de4b-105">Members</span></span>  
  
|<span data-ttu-id="6de4b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6de4b-106">Member</span></span>|<span data-ttu-id="6de4b-107">Description</span><span class="sxs-lookup"><span data-stu-id="6de4b-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="6de4b-108">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="6de4b-108">Default value.</span></span> <span data-ttu-id="6de4b-109">Comme pour `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="6de4b-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="6de4b-110">Indique qu’un verrou de lecteur/writer ne peut pas être défini.</span><span class="sxs-lookup"><span data-stu-id="6de4b-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="6de4b-111">Indique qu’un verrou de lecteur/writer peut être défini.</span><span class="sxs-lookup"><span data-stu-id="6de4b-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6de4b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6de4b-112">Requirements</span></span>  
 <span data-ttu-id="6de4b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de4b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de4b-114">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6de4b-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6de4b-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de4b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de4b-116">See Also</span></span>  
 [<span data-ttu-id="6de4b-117">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6de4b-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
