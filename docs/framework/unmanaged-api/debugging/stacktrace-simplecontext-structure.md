---
title: StackTrace_SimpleContext
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackTrace_SimpleContext
api_location: diasymreader.dll
api_type: COM
f1_keywords: SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87ce3d50d6da6a7c23b13fa10123033efbb6c52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="0c49f-102">StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="0c49f-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="0c49f-103">Fournit un contexte simple qui peut être utilisé à la place d'une structure `CONTEXT` complète.</span><span class="sxs-lookup"><span data-stu-id="0c49f-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c49f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c49f-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="0c49f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0c49f-105">Members</span></span>  
  
|<span data-ttu-id="0c49f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0c49f-106">Member</span></span>|<span data-ttu-id="0c49f-107">Description</span><span class="sxs-lookup"><span data-stu-id="0c49f-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="0c49f-108">Le pointeur de pile, ou le pointeur de pile d’entrée (ESP) sur x86 plateformes.</span><span class="sxs-lookup"><span data-stu-id="0c49f-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="0c49f-109">Offset de frame ou EBP sur x86 les plateformes.</span><span class="sxs-lookup"><span data-stu-id="0c49f-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="0c49f-110">Le pointeur d’instruction, ou que le pointeur d’instruction (EIP) entrée sur x86 plateformes.</span><span class="sxs-lookup"><span data-stu-id="0c49f-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c49f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="0c49f-111">Remarks</span></span>  
 <span data-ttu-id="0c49f-112">Étant donné que les fonctions de trace de pile doivent généralement retourner uniquement l’adresse offset de frame et adresse de la pile, vous pouvez éventuellement utiliser le `SimpleContext` structure au lieu d’un grand `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="0c49f-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c49f-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0c49f-113">Requirements</span></span>  
 <span data-ttu-id="0c49f-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c49f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c49f-115">**En-tête :** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="0c49f-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="0c49f-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c49f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c49f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c49f-117">See Also</span></span>  
 [<span data-ttu-id="0c49f-118">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="0c49f-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="0c49f-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="0c49f-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
