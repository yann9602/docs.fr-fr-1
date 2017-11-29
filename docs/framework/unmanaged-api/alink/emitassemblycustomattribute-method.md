---
title: "EmitAssemblyCustomAttribute, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssemblyCustomAttribute
helpviewer_keywords: EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb21ee1396a9dd0426b9b91711c2345ef66c09f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="c1da5-102">EmitAssemblyCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="c1da5-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="c1da5-103">L’appel à définir les attributs de niveau assembly.</span><span class="sxs-lookup"><span data-stu-id="c1da5-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1da5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1da5-104">Syntax</span></span>  
  
```  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1da5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1da5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c1da5-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c1da5-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c1da5-107">Fichier qui définit l’attribut.</span><span class="sxs-lookup"><span data-stu-id="c1da5-107">File that defiles the attribute.</span></span> <span data-ttu-id="c1da5-108">Peut être NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="c1da5-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c1da5-109">Type de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c1da5-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="c1da5-110">Valeur des données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c1da5-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="c1da5-111">Longueur des données de valeur personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c1da5-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="c1da5-112">TRUE si l’attribut personnalisé est associée à la signature de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c1da5-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="c1da5-113">TRUE si plusieurs attributs doivent être émises.</span><span class="sxs-lookup"><span data-stu-id="c1da5-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1da5-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1da5-114">Return Value</span></span>  
 <span data-ttu-id="c1da5-115">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="c1da5-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1da5-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c1da5-116">Requirements</span></span>  
 <span data-ttu-id="c1da5-117">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="c1da5-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1da5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1da5-118">See Also</span></span>  
 [<span data-ttu-id="c1da5-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c1da5-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c1da5-120">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="c1da5-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c1da5-121">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="c1da5-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
