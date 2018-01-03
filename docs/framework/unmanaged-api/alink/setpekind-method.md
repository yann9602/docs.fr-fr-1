---
title: "SetPEKind, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetPEKind
api_location: alink.dll
api_type: COM
f1_keywords: SetPEKind
helpviewer_keywords: SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ad300d86dadd470d0a2d50d5d6deac5bd0bad71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setpekind-method"></a><span data-ttu-id="b591e-102">SetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="b591e-102">SetPEKind Method</span></span>
<span data-ttu-id="b591e-103">Détermine le type exécutable portable, un ordinateur ou spécifique à indépendant de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b591e-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b591e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b591e-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="b591e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b591e-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b591e-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b591e-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b591e-107">Jeton du fichier pour lequel le type PE doit être défini.</span><span class="sxs-lookup"><span data-stu-id="b591e-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="b591e-108">Peut être NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="b591e-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="b591e-109">Le type de PE, tel qu’indiqué par le [CorPEKind, énumération](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b591e-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="b591e-110">L’architecture d’ordinateur cible, comme indiqué dans l’en-tête NT.</span><span class="sxs-lookup"><span data-stu-id="b591e-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b591e-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b591e-111">Return Value</span></span>  
 <span data-ttu-id="b591e-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="b591e-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b591e-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b591e-113">Requirements</span></span>  
 <span data-ttu-id="b591e-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="b591e-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b591e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b591e-115">See Also</span></span>  
 [<span data-ttu-id="b591e-116">GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="b591e-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="b591e-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="b591e-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b591e-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="b591e-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b591e-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="b591e-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
