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
ms.workload: dotnet
ms.openlocfilehash: 9cc7709ef060642f12a8bc7d048e520427a5c674
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="0a3e4-102">EmitAssemblyCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="0a3e4-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="0a3e4-103">L’appel à définir les attributs de niveau assembly.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a3e4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0a3e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a3e4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0a3e4-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0a3e4-107">Fichier qui définit l’attribut.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-107">File that defiles the attribute.</span></span> <span data-ttu-id="0a3e4-108">Peut être NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="0a3e4-109">Type de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="0a3e4-110">Valeur des données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="0a3e4-111">Longueur des données de valeur personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="0a3e4-112">TRUE si l’attribut personnalisé est associée à la signature de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="0a3e4-113">TRUE si plusieurs attributs doivent être émises.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a3e4-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0a3e4-114">Return Value</span></span>  
 <span data-ttu-id="0a3e4-115">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="0a3e4-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a3e4-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0a3e4-116">Requirements</span></span>  
 <span data-ttu-id="0a3e4-117">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="0a3e4-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3e4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a3e4-118">See Also</span></span>  
 [<span data-ttu-id="0a3e4-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="0a3e4-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0a3e4-120">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="0a3e4-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0a3e4-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="0a3e4-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
