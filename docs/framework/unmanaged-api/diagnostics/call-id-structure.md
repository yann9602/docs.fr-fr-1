---
title: CALL_ID, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CALL_ID
api_location: diasymreader.dll
api_type: COM
f1_keywords: CALL_ID
helpviewer_keywords: CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c44db9021a7dbf5b497db3536eddcea020e71bf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="callid-structure"></a><span data-ttu-id="088bb-102">CALL_ID, structure</span><span class="sxs-lookup"><span data-stu-id="088bb-102">CALL_ID Structure</span></span>
<span data-ttu-id="088bb-103">Fournit des informations à un débogueur sur une fonction qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="088bb-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="088bb-104">Consultez le [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="088bb-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="088bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="088bb-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="088bb-106">Membres</span><span class="sxs-lookup"><span data-stu-id="088bb-106">Members</span></span>  
  
|<span data-ttu-id="088bb-107">Membre</span><span class="sxs-lookup"><span data-stu-id="088bb-107">Member</span></span>|<span data-ttu-id="088bb-108">Description</span><span class="sxs-lookup"><span data-stu-id="088bb-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="088bb-109">Identifie l’ordinateur qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="088bb-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="088bb-110">Identifie le processeur de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="088bb-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="088bb-111">Identifie le thread qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="088bb-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="088bb-112">Spécifie l’adresse de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="088bb-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="088bb-113">Spécifie l’adresse de l’appel.</span><span class="sxs-lookup"><span data-stu-id="088bb-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="088bb-114">Identifie l’ordinateur qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="088bb-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="088bb-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="088bb-115">Requirements</span></span>  
 <span data-ttu-id="088bb-116">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="088bb-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="088bb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="088bb-117">See Also</span></span>  
 [<span data-ttu-id="088bb-118">INotifySink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="088bb-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="088bb-119">Structures du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="088bb-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
