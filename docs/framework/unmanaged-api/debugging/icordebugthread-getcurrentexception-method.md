---
title: "ICorDebugThread::GetCurrentException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="01212-102">ICorDebugThread::GetCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="01212-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="01212-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception levée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="01212-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01212-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01212-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01212-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01212-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="01212-106">[out] Un pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente l’exception levée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="01212-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01212-107">Notes</span><span class="sxs-lookup"><span data-stu-id="01212-107">Remarks</span></span>  
 <span data-ttu-id="01212-108">L’objet exception existe à partir de l’heure de l’exception est levée jusqu'à la fin de la `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="01212-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="01212-109">Une évaluation de fonction, qui est effectuée par les méthodes ICorDebugEval, efface l’objet exception sur le programme d’installation et restaurez-la à la fin.</span><span class="sxs-lookup"><span data-stu-id="01212-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="01212-110">Les exceptions peuvent être imbriquées (par exemple, si une exception est levée dans un filtre ou dans une évaluation de fonction), afin qu’il peut y avoir plusieurs exceptions en attente sur un thread unique.</span><span class="sxs-lookup"><span data-stu-id="01212-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="01212-111">`GetCurrentException`Retourne l’exception la plus récente.</span><span class="sxs-lookup"><span data-stu-id="01212-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="01212-112">L’objet exception et le type peuvent changer pendant toute la vie de l’exception.</span><span class="sxs-lookup"><span data-stu-id="01212-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="01212-113">Par exemple, après qu’une exception de type x est levée, le common language runtime (CLR) peut manquer de mémoire et promouvoir en une exception de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="01212-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01212-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01212-114">Requirements</span></span>  
 <span data-ttu-id="01212-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01212-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01212-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01212-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01212-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01212-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01212-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01212-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
