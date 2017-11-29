---
title: "CorMethodSemanticsAttr, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodSemanticsAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodSemanticsAttr
helpviewer_keywords: CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c6dca24aad06b1c07c86cb716f4be344c8458471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="8b89a-102">CorMethodSemanticsAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="8b89a-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="8b89a-103">Contient des valeurs qui décrivent la relation entre une méthode et une propriété ou un événement associé.</span><span class="sxs-lookup"><span data-stu-id="8b89a-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b89a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b89a-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="8b89a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8b89a-105">Members</span></span>  
  
|<span data-ttu-id="8b89a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="8b89a-106">Member</span></span>|<span data-ttu-id="8b89a-107">Description</span><span class="sxs-lookup"><span data-stu-id="8b89a-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="8b89a-108">Spécifie que la méthode est un `set` accesseur pour une propriété.</span><span class="sxs-lookup"><span data-stu-id="8b89a-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="8b89a-109">Spécifie que la méthode est un `get` accesseur pour une propriété.</span><span class="sxs-lookup"><span data-stu-id="8b89a-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="8b89a-110">Spécifie que la méthode a une relation à une propriété ou un événement autres que ceux définis ici.</span><span class="sxs-lookup"><span data-stu-id="8b89a-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="8b89a-111">Spécifie que la méthode ajoute des méthodes de gestionnaire pour un événement.</span><span class="sxs-lookup"><span data-stu-id="8b89a-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="8b89a-112">Spécifie que la méthode supprime les méthodes de gestionnaire pour un événement.</span><span class="sxs-lookup"><span data-stu-id="8b89a-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="8b89a-113">Spécifie que la méthode déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="8b89a-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b89a-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8b89a-114">Requirements</span></span>  
 <span data-ttu-id="8b89a-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b89a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b89a-116">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8b89a-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8b89a-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b89a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b89a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b89a-118">See Also</span></span>  
 [<span data-ttu-id="8b89a-119">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="8b89a-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
