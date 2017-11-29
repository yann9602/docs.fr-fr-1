---
title: "EmitAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssembly
helpviewer_keywords: EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3471c4ad2d06443e0f05dc344be5f791817f2d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="bd9e3-102">EmitAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="bd9e3-102">EmitAssembly Method</span></span>
<span data-ttu-id="bd9e3-103">Crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bd9e3-103">Creates the assembly.</span></span> <span data-ttu-id="bd9e3-104">Appelez cette méthode après la fermeture de tous les autres fichiers à l’exception du fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bd9e3-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="bd9e3-105">N’appelez pas cette méthode lors de la production de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="bd9e3-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9e3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd9e3-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd9e3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd9e3-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bd9e3-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bd9e3-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd9e3-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bd9e3-109">Return Value</span></span>  
 <span data-ttu-id="bd9e3-110">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="bd9e3-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd9e3-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bd9e3-111">Requirements</span></span>  
 <span data-ttu-id="bd9e3-112">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="bd9e3-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9e3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd9e3-113">See Also</span></span>  
 [<span data-ttu-id="bd9e3-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="bd9e3-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bd9e3-115">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="bd9e3-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bd9e3-116">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="bd9e3-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
