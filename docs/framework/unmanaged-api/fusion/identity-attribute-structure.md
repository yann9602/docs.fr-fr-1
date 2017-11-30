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
ms.openlocfilehash: 3fc4d9f7a95a3283d87f036163592f43e87dd053
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="04d06-102">IDENTITY_ATTRIBUTE, structure</span><span class="sxs-lookup"><span data-stu-id="04d06-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="04d06-103">Contient des informations sur les attributs de métadonnées sur une [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="04d06-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04d06-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="04d06-105">Membres</span><span class="sxs-lookup"><span data-stu-id="04d06-105">Members</span></span>  
  
|<span data-ttu-id="04d06-106">Membre</span><span class="sxs-lookup"><span data-stu-id="04d06-106">Member</span></span>|<span data-ttu-id="04d06-107">Description</span><span class="sxs-lookup"><span data-stu-id="04d06-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="04d06-108">Un pointeur vers une chaîne de caractères terminée par null qui contient l’espace de noms est de l’attribut dans.</span><span class="sxs-lookup"><span data-stu-id="04d06-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="04d06-109">Un pointeur vers une chaîne de caractères terminée par null qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="04d06-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="04d06-110">Un pointeur vers une chaîne de caractères terminée par null qui contient la valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="04d06-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04d06-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="04d06-111">Remarks</span></span>  
 <span data-ttu-id="04d06-112">Le `IDENTITY_ATTRIBUTE` structure contient trois pointeurs vers des chaînes de caractères terminée par null.</span><span class="sxs-lookup"><span data-stu-id="04d06-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="04d06-113">Ces trois chaînes décrivent un attribut.</span><span class="sxs-lookup"><span data-stu-id="04d06-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="04d06-114">Une instance d’un `IDENTITY_ATTRIBUTE` structure est associée à une instance d’un [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="04d06-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="04d06-115">Le `IDENTITY_ATTRIBUTE` structure contient les chaînes réelles et correspondants `IDENTITY_ATTRIBUTE_BLOB` structure répertorie les offsets pour les trois chaînes répertoriées dans le `IDENTITY_ATTRIBUTE` structure.</span><span class="sxs-lookup"><span data-stu-id="04d06-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d06-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04d06-116">Requirements</span></span>  
 <span data-ttu-id="04d06-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04d06-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d06-118">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="04d06-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="04d06-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d06-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d06-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04d06-120">See Also</span></span>  
 [<span data-ttu-id="04d06-121">IDefinitionIdentity (Interface)</span><span class="sxs-lookup"><span data-stu-id="04d06-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="04d06-122">IDENTITY_ATTRIBUTE_BLOB (Structure)</span><span class="sxs-lookup"><span data-stu-id="04d06-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="04d06-123">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="04d06-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
