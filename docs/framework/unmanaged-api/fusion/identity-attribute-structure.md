---
title: IDENTITY_ATTRIBUTE, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="00faf-102">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="00faf-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="00faf-103">Contient des informations sur les attributs de métadonnées sur une [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="00faf-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00faf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00faf-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="00faf-105">Membres</span><span class="sxs-lookup"><span data-stu-id="00faf-105">Members</span></span>  
  
|<span data-ttu-id="00faf-106">Membre</span><span class="sxs-lookup"><span data-stu-id="00faf-106">Member</span></span>|<span data-ttu-id="00faf-107">Description</span><span class="sxs-lookup"><span data-stu-id="00faf-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="00faf-108">Un pointeur vers une chaîne de caractères terminée par null qui contient l’espace de noms est de l’attribut dans.</span><span class="sxs-lookup"><span data-stu-id="00faf-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="00faf-109">Un pointeur vers une chaîne de caractères terminée par null qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="00faf-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="00faf-110">Un pointeur vers une chaîne de caractères terminée par null qui contient la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="00faf-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00faf-111">Notes</span><span class="sxs-lookup"><span data-stu-id="00faf-111">Remarks</span></span>  
 <span data-ttu-id="00faf-112">Le `IDENTITY_ATTRIBUTE` structure contient trois pointeurs vers des chaînes de caractères terminée par null.</span><span class="sxs-lookup"><span data-stu-id="00faf-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="00faf-113">Ces trois chaînes décrivent un attribut.</span><span class="sxs-lookup"><span data-stu-id="00faf-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="00faf-114">Une instance d’un `IDENTITY_ATTRIBUTE` structure est associée à une instance d’un [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="00faf-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="00faf-115">Le `IDENTITY_ATTRIBUTE` structure contient les chaînes réelles et correspondants `IDENTITY_ATTRIBUTE_BLOB` structure répertorie les offsets pour les trois chaînes répertoriées dans le `IDENTITY_ATTRIBUTE` structure.</span><span class="sxs-lookup"><span data-stu-id="00faf-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00faf-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00faf-116">Requirements</span></span>  
 <span data-ttu-id="00faf-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00faf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00faf-118">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="00faf-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="00faf-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00faf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00faf-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00faf-120">See Also</span></span>  
 [<span data-ttu-id="00faf-121">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="00faf-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="00faf-122">IDENTITY_ATTRIBUTE_BLOB, structure</span><span class="sxs-lookup"><span data-stu-id="00faf-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="00faf-123">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="00faf-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
