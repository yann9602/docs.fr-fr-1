---
title: "PreCloseAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d940cbdeddc7030c679fae8c8694bb3542123b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="0717a-102">PreCloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="0717a-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="0717a-103">Ferme le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0717a-103">Closes the assembly file.</span></span> <span data-ttu-id="0717a-104">Appelez cette méthode après la fermeture de tous les autres fichiers, mais avant de fermer le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0717a-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="0717a-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="0717a-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0717a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0717a-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0717a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0717a-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0717a-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0717a-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0717a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0717a-109">Return Value</span></span>  
 <span data-ttu-id="0717a-110">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="0717a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0717a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0717a-111">Requirements</span></span>  
 <span data-ttu-id="0717a-112">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="0717a-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0717a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0717a-113">See Also</span></span>  
 [<span data-ttu-id="0717a-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="0717a-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0717a-115">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0717a-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0717a-116">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="0717a-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
