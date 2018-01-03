---
title: "EndMerge, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EndMerge
- EndMerge
api_location: alink.dll
api_type: COM
f1_keywords: EndMerge
helpviewer_keywords: EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58e9cecae43fb69f1ce2e90eb9d6551d287ca7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="endmerge-method"></a><span data-ttu-id="4ac44-102">EndMerge, méthode</span><span class="sxs-lookup"><span data-stu-id="4ac44-102">EndMerge Method</span></span>
<span data-ttu-id="4ac44-103">Indique que tous les attributs personnalisés ont été fusionnées dans la portée d’émission.</span><span class="sxs-lookup"><span data-stu-id="4ac44-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ac44-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ac44-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4ac44-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4ac44-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4ac44-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ac44-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4ac44-107">Return Value</span></span>  
 <span data-ttu-id="4ac44-108">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="4ac44-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ac44-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4ac44-109">Requirements</span></span>  
 <span data-ttu-id="4ac44-110">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="4ac44-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac44-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ac44-111">See Also</span></span>  
 [<span data-ttu-id="4ac44-112">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="4ac44-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4ac44-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="4ac44-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4ac44-114">API ALink</span><span class="sxs-lookup"><span data-stu-id="4ac44-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
