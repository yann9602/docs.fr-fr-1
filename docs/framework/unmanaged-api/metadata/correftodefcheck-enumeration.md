---
title: "CorRefToDefCheck, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5144cd3ac261647c04ec7e3e27e28618c94fb439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="44d86-102">CorRefToDefCheck, énumération</span><span class="sxs-lookup"><span data-stu-id="44d86-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="44d86-103">Spécifie des indicateurs pour contrôler les éléments référencés qui sont convertis en définitions afin d'optimiser le code.</span><span class="sxs-lookup"><span data-stu-id="44d86-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44d86-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="44d86-105">Membres</span><span class="sxs-lookup"><span data-stu-id="44d86-105">Members</span></span>  
  
|<span data-ttu-id="44d86-106">Membre</span><span class="sxs-lookup"><span data-stu-id="44d86-106">Member</span></span>|<span data-ttu-id="44d86-107">Description</span><span class="sxs-lookup"><span data-stu-id="44d86-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="44d86-108">Spécifie que les références de type et les références de membre doivent être convertis aux définitions.</span><span class="sxs-lookup"><span data-stu-id="44d86-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="44d86-109">C’est la valeur par défaut (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="44d86-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="44d86-110">Spécifie que tous les éléments référencés doivent être convertis en définitions.</span><span class="sxs-lookup"><span data-stu-id="44d86-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="44d86-111">Spécifie qu’aucun élément référencé ne doit être convertis en définitions.</span><span class="sxs-lookup"><span data-stu-id="44d86-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="44d86-112">Spécifie que seules les références de type doivent être convertis en définitions de type.</span><span class="sxs-lookup"><span data-stu-id="44d86-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="44d86-113">Spécifie que seules les références de membre doivent être convertis aux définitions.</span><span class="sxs-lookup"><span data-stu-id="44d86-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="44d86-114">Autrement dit, les références de membre doivent être converties à des définitions de méthode ou de définitions de champ.</span><span class="sxs-lookup"><span data-stu-id="44d86-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44d86-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="44d86-115">Requirements</span></span>  
 <span data-ttu-id="44d86-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44d86-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d86-117">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="44d86-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="44d86-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d86-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d86-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44d86-119">See Also</span></span>  
 [<span data-ttu-id="44d86-120">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="44d86-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
