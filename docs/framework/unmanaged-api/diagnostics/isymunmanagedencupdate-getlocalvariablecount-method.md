---
title: "ISymUnmanagedENCUpdate::GetLocalVariableCount, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c86b2988d414d091bc23d29bd79f518a756d688
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="2252f-102">ISymUnmanagedENCUpdate::GetLocalVariableCount, méthode</span><span class="sxs-lookup"><span data-stu-id="2252f-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="2252f-103">Obtient le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="2252f-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2252f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2252f-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2252f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2252f-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="2252f-106">[in] Le jeton de métadonnées de méthodes.</span><span class="sxs-lookup"><span data-stu-id="2252f-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="2252f-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="2252f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2252f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2252f-108">Return Value</span></span>  
 <span data-ttu-id="2252f-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2252f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2252f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2252f-110">Requirements</span></span>  
 <span data-ttu-id="2252f-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2252f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2252f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2252f-112">See Also</span></span>  
 [<span data-ttu-id="2252f-113">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="2252f-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
