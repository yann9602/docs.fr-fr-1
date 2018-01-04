---
title: "CorLocalRefPreservation, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLocalRefPreservation
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLocalRefPreservation
helpviewer_keywords: CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c35bbfef62f65a9a401d00f9ae56e2f4c00bb0b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="4b16c-102">CorLocalRefPreservation, énumération</span><span class="sxs-lookup"><span data-stu-id="4b16c-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="4b16c-103">Contient des valeurs d'indicateur pour le traitement des références locales.</span><span class="sxs-lookup"><span data-stu-id="4b16c-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b16c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b16c-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="4b16c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="4b16c-105">Members</span></span>  
  
|<span data-ttu-id="4b16c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="4b16c-106">Member</span></span>|<span data-ttu-id="4b16c-107">Description</span><span class="sxs-lookup"><span data-stu-id="4b16c-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="4b16c-108">Ne conserver aucune référence locale.</span><span class="sxs-lookup"><span data-stu-id="4b16c-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="4b16c-109">Conserver les références de type local.</span><span class="sxs-lookup"><span data-stu-id="4b16c-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="4b16c-110">Conserver les références de membre locale.</span><span class="sxs-lookup"><span data-stu-id="4b16c-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b16c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4b16c-111">Requirements</span></span>  
 <span data-ttu-id="4b16c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b16c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b16c-113">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4b16c-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4b16c-114">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b16c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b16c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b16c-115">See Also</span></span>  
 [<span data-ttu-id="4b16c-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="4b16c-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
