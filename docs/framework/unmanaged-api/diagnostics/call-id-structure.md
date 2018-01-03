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
ms.workload: dotnet
ms.openlocfilehash: 71fd69cbcced1440839b9eedf8fbe3d8f5b90646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="callid-structure"></a><span data-ttu-id="ff322-102">CALL_ID, structure</span><span class="sxs-lookup"><span data-stu-id="ff322-102">CALL_ID Structure</span></span>
<span data-ttu-id="ff322-103">Fournit des informations à un débogueur sur une fonction qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="ff322-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="ff322-104">Consultez le [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="ff322-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff322-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff322-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ff322-106">Membres</span><span class="sxs-lookup"><span data-stu-id="ff322-106">Members</span></span>  
  
|<span data-ttu-id="ff322-107">Membre</span><span class="sxs-lookup"><span data-stu-id="ff322-107">Member</span></span>|<span data-ttu-id="ff322-108">Description</span><span class="sxs-lookup"><span data-stu-id="ff322-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="ff322-109">Identifie l’ordinateur qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="ff322-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="ff322-110">Identifie le processeur de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ff322-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="ff322-111">Identifie le thread qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="ff322-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="ff322-112">Spécifie l’adresse de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="ff322-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="ff322-113">Spécifie l’adresse de l’appel.</span><span class="sxs-lookup"><span data-stu-id="ff322-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="ff322-114">Identifie l’ordinateur qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="ff322-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff322-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff322-115">Requirements</span></span>  
 <span data-ttu-id="ff322-116">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="ff322-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff322-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff322-117">See Also</span></span>  
 [<span data-ttu-id="ff322-118">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="ff322-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="ff322-119">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="ff322-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
