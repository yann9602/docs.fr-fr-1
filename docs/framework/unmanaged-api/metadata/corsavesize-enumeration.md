---
title: "CorSaveSize, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSaveSize
helpviewer_keywords: CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3780050285f63fa7334ec5463cd22050836dc136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="4a28c-102">CorSaveSize, énumération</span><span class="sxs-lookup"><span data-stu-id="4a28c-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="4a28c-103">Contient des valeurs indiquant le niveau de précision requis lors de l'interrogation de la taille d'une opération d'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="4a28c-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a28c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a28c-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="4a28c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="4a28c-105">Members</span></span>  
  
|<span data-ttu-id="4a28c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="4a28c-106">Member</span></span>|<span data-ttu-id="4a28c-107">Description</span><span class="sxs-lookup"><span data-stu-id="4a28c-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="4a28c-108">Spécifie que la valeur de retour doit être exacte.</span><span class="sxs-lookup"><span data-stu-id="4a28c-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="4a28c-109">Spécifie que la valeur de retour doit être estimée.</span><span class="sxs-lookup"><span data-stu-id="4a28c-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="4a28c-110">Spécifie que les types pouvant être éliminées doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="4a28c-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a28c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4a28c-111">Requirements</span></span>  
 <span data-ttu-id="4a28c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a28c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a28c-113">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4a28c-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4a28c-114">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a28c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a28c-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a28c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a28c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a28c-116">See Also</span></span>  
 [<span data-ttu-id="4a28c-117">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="4a28c-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
