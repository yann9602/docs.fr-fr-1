---
title: CodeChunkInfo Structure1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CodeChunkInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: CodeChunkInfo
helpviewer_keywords: CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7b3b858d645f01f58ba0b67465b22dd05282656
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="e948c-102">CodeChunkInfo Structure1</span><span class="sxs-lookup"><span data-stu-id="e948c-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="e948c-103">Représente un bloc de code unique en mémoire.</span><span class="sxs-lookup"><span data-stu-id="e948c-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e948c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e948c-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e948c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e948c-105">Members</span></span>  
  
|<span data-ttu-id="e948c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e948c-106">Member</span></span>|<span data-ttu-id="e948c-107">Description</span><span class="sxs-lookup"><span data-stu-id="e948c-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="e948c-108">A `CORDB_ADDRESS` valeur qui spécifie l’adresse de départ du segment.</span><span class="sxs-lookup"><span data-stu-id="e948c-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="e948c-109">La taille, en octets, du segment.</span><span class="sxs-lookup"><span data-stu-id="e948c-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e948c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e948c-110">Remarks</span></span>  
 <span data-ttu-id="e948c-111">Le segment de code unique est une région de code natif qui fait partie d’un objet de code comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="e948c-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e948c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e948c-112">Requirements</span></span>  
 <span data-ttu-id="e948c-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e948c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e948c-114">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="e948c-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e948c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e948c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e948c-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e948c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e948c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e948c-117">See Also</span></span>  
 [<span data-ttu-id="e948c-118">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="e948c-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="e948c-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="e948c-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="e948c-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="e948c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
