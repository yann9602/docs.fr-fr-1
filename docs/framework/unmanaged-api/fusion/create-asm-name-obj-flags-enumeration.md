---
title: "CREATE_ASM_NAME_OBJ_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4982b33643d855be4b8cace59f1c5cac4201d5ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="7ee32-102">CREATE_ASM_NAME_OBJ_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="7ee32-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="7ee32-103">Spécifie les attributs d’un [IAssemblyName (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) de l’objet lorsqu’il est construit par la [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="7ee32-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ee32-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7ee32-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7ee32-105">Members</span></span>  
  
|<span data-ttu-id="7ee32-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7ee32-106">Member</span></span>|<span data-ttu-id="7ee32-107">Description</span><span class="sxs-lookup"><span data-stu-id="7ee32-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="7ee32-108">Indique que le paramètre passé est une identité textuelle.</span><span class="sxs-lookup"><span data-stu-id="7ee32-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="7ee32-109">Définit le nombre de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="7ee32-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="7ee32-110">Vérifie la règle d’assembly friend (uniquement un nom et clé publique).</span><span class="sxs-lookup"><span data-stu-id="7ee32-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="7ee32-111">Ce membre est à usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="7ee32-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="7ee32-112">Une combinaison de la `CANOF_PARSE_DISPLAY_NAME` et `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` indicateurs.</span><span class="sxs-lookup"><span data-stu-id="7ee32-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="7ee32-113">Ce membre est à usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="7ee32-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ee32-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7ee32-114">Requirements</span></span>  
 <span data-ttu-id="7ee32-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ee32-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee32-116">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7ee32-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7ee32-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee32-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ee32-118">See Also</span></span>  
 [<span data-ttu-id="7ee32-119">IAssemblyName (Interface)</span><span class="sxs-lookup"><span data-stu-id="7ee32-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="7ee32-120">CreateAssemblyNameObject (fonction)</span><span class="sxs-lookup"><span data-stu-id="7ee32-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [<span data-ttu-id="7ee32-121">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="7ee32-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
