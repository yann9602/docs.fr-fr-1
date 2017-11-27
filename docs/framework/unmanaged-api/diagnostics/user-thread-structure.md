---
title: USER_THREAD, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: USER_THREAD
api_location: diasymreader.dll
api_type: COM
f1_keywords: USER_THREAD
helpviewer_keywords: USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d93002fe5460bfdb36d4e11c74410677b46a98d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="05ed3-102">USER_THREAD, structure</span><span class="sxs-lookup"><span data-stu-id="05ed3-102">USER_THREAD Structure</span></span>
<span data-ttu-id="05ed3-103">Fournit des informations à un débogueur sur un thread.</span><span class="sxs-lookup"><span data-stu-id="05ed3-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="05ed3-104">Pour plus d’informations, consultez la [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="05ed3-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ed3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ed3-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="05ed3-106">Membres</span><span class="sxs-lookup"><span data-stu-id="05ed3-106">Members</span></span>  
  
|<span data-ttu-id="05ed3-107">Membre</span><span class="sxs-lookup"><span data-stu-id="05ed3-107">Member</span></span>|<span data-ttu-id="05ed3-108">Description</span><span class="sxs-lookup"><span data-stu-id="05ed3-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="05ed3-109">Adresse de la mémoire tampon de thread.</span><span class="sxs-lookup"><span data-stu-id="05ed3-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="05ed3-110">Longueur de la mémoire tampon de thread, en octets.</span><span class="sxs-lookup"><span data-stu-id="05ed3-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="05ed3-111">ID de thread.</span><span class="sxs-lookup"><span data-stu-id="05ed3-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05ed3-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="05ed3-112">Requirements</span></span>  
 <span data-ttu-id="05ed3-113">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="05ed3-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ed3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05ed3-114">See Also</span></span>  
 [<span data-ttu-id="05ed3-115">SetNotifyFilter (méthode)</span><span class="sxs-lookup"><span data-stu-id="05ed3-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="05ed3-116">Structures du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="05ed3-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
