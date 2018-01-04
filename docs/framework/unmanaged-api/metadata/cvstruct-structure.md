---
title: CVStruct, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CVStruct
api_location: mscoree.dll
api_type: COM
f1_keywords: CVStruct
helpviewer_keywords: CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e0c9087b180b39185fbf66235b515b9742e69ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="d81f4-102">CVStruct, structure</span><span class="sxs-lookup"><span data-stu-id="d81f4-102">CVStruct Structure</span></span>
<span data-ttu-id="d81f4-103">Contient des informations utilisées lors de l'installation d'un module ou d'une image composite.</span><span class="sxs-lookup"><span data-stu-id="d81f4-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d81f4-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="d81f4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d81f4-105">Members</span></span>  
  
|<span data-ttu-id="d81f4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d81f4-106">Member</span></span>|<span data-ttu-id="d81f4-107">Description</span><span class="sxs-lookup"><span data-stu-id="d81f4-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d81f4-108">Majeur</span><span class="sxs-lookup"><span data-stu-id="d81f4-108">Major</span></span>|<span data-ttu-id="d81f4-109">Numéro de version majeure.</span><span class="sxs-lookup"><span data-stu-id="d81f4-109">Major version build number.</span></span>|  
|<span data-ttu-id="d81f4-110">Mineur</span><span class="sxs-lookup"><span data-stu-id="d81f4-110">Minor</span></span>|<span data-ttu-id="d81f4-111">Numéro de version mineure.</span><span class="sxs-lookup"><span data-stu-id="d81f4-111">Minor version build number.</span></span>|  
|<span data-ttu-id="d81f4-112">Sub</span><span class="sxs-lookup"><span data-stu-id="d81f4-112">Sub</span></span>|<span data-ttu-id="d81f4-113">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="d81f4-113">Sub-build number.</span></span>|  
|<span data-ttu-id="d81f4-114">Générer</span><span class="sxs-lookup"><span data-stu-id="d81f4-114">Build</span></span>|<span data-ttu-id="d81f4-115">Numéro de build.</span><span class="sxs-lookup"><span data-stu-id="d81f4-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d81f4-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d81f4-116">Requirements</span></span>  
 <span data-ttu-id="d81f4-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d81f4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d81f4-118">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d81f4-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d81f4-119">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d81f4-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d81f4-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d81f4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d81f4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d81f4-121">See Also</span></span>  
 [<span data-ttu-id="d81f4-122">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="d81f4-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
