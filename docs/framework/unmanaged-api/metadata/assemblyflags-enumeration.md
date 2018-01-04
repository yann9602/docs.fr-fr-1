---
title: "AssemblyFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 605817ef23246f708b6cf46a93072cde3003ab43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="8929c-102">AssemblyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="8929c-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="8929c-103">Contient des valeurs qui décrivent les fonctionnalités d’exécution d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="8929c-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8929c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8929c-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8929c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8929c-105">Members</span></span>  
  
|<span data-ttu-id="8929c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="8929c-106">Member</span></span>|<span data-ttu-id="8929c-107">Description</span><span class="sxs-lookup"><span data-stu-id="8929c-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="8929c-108">Spécifie que les définitions de types exportés sont implicites dans les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8929c-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="8929c-109">Dans les versions 1.0 et 1.1 du .NET Framework, cette valeur est toujours supposée être définie.</span><span class="sxs-lookup"><span data-stu-id="8929c-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="8929c-110">Spécifie que les définitions de ressources sont implicites dans les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8929c-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="8929c-111">Dans le .NET Framework 1.0 et 1.1, cette valeur est toujours supposée être définie.</span><span class="sxs-lookup"><span data-stu-id="8929c-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="8929c-112">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8929c-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="8929c-113">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="8929c-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="8929c-114">Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles sont en cours d’exécution sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8929c-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8929c-115">Notes</span><span class="sxs-lookup"><span data-stu-id="8929c-115">Remarks</span></span>  
 <span data-ttu-id="8929c-116">Les valeurs comprises entre 0 x 0010 et 0 x 0070 inclus, sont utilisés pour décrire les fonctionnalités de compatibilité de la côte à côte de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="8929c-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="8929c-117">Si aucune de ces valeurs sont définies, l’assembly est supposé être compatible avec le côte à côte.</span><span class="sxs-lookup"><span data-stu-id="8929c-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8929c-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8929c-118">Requirements</span></span>  
 <span data-ttu-id="8929c-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8929c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8929c-120">**En-tête :** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8929c-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="8929c-121">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8929c-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8929c-122">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8929c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8929c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8929c-123">See Also</span></span>  
 [<span data-ttu-id="8929c-124">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="8929c-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="8929c-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8929c-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
