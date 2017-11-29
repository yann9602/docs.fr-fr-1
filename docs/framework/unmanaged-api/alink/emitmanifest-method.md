---
title: "EmitManifest, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03ef815f03a65cbf7e2dc936b21848e206132add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="30dfa-102">EmitManifest, méthode</span><span class="sxs-lookup"><span data-stu-id="30dfa-102">EmitManifest Method</span></span>
<span data-ttu-id="30dfa-103">Émet le manifeste final.</span><span class="sxs-lookup"><span data-stu-id="30dfa-103">Emits the final manifest.</span></span> <span data-ttu-id="30dfa-104">Appelez cette méthode après l’importation de tous les autres fichiers et la définition de toutes les options.</span><span class="sxs-lookup"><span data-stu-id="30dfa-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="30dfa-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="30dfa-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30dfa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30dfa-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30dfa-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30dfa-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="30dfa-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30dfa-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="30dfa-109">Reçoit la taille à réserver dans le fichier d’assembly, récupérée à partir de [StrongNameSignatureSize, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="30dfa-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="30dfa-110">Si vous le souhaitez reçoit le jeton de manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="30dfa-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30dfa-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="30dfa-111">Return Value</span></span>  
 <span data-ttu-id="30dfa-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="30dfa-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30dfa-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="30dfa-113">Requirements</span></span>  
 <span data-ttu-id="30dfa-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="30dfa-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dfa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30dfa-115">See Also</span></span>  
 [<span data-ttu-id="30dfa-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="30dfa-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="30dfa-117">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="30dfa-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="30dfa-118">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="30dfa-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
