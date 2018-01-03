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
ms.workload: dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="ce840-102">EmitAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="ce840-102">EmitAssembly Method</span></span>
<span data-ttu-id="ce840-103">Crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce840-103">Creates the assembly.</span></span> <span data-ttu-id="ce840-104">Appelez cette méthode après la fermeture de tous les autres fichiers à l’exception du fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce840-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="ce840-105">N’appelez pas cette méthode lors de la production de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="ce840-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce840-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce840-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce840-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce840-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ce840-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce840-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce840-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ce840-109">Return Value</span></span>  
 <span data-ttu-id="ce840-110">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="ce840-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce840-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce840-111">Requirements</span></span>  
 <span data-ttu-id="ce840-112">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="ce840-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce840-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce840-113">See Also</span></span>  
 [<span data-ttu-id="ce840-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="ce840-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ce840-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="ce840-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ce840-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="ce840-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
