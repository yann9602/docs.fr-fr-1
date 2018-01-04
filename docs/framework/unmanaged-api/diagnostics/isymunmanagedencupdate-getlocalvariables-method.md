---
title: "ISymUnmanagedENCUpdate::GetLocalVariables, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eefd64441221a7e6e00689d6be272540f9c2423c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="88892-102">ISymUnmanagedENCUpdate::GetLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="88892-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="88892-103">Obtient les variables locales.</span><span class="sxs-lookup"><span data-stu-id="88892-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88892-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88892-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88892-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88892-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="88892-106">[in] Le jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="88892-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="88892-107">[in] A `ULONG` qui indique la taille de la `rgLocals` paramètre.</span><span class="sxs-lookup"><span data-stu-id="88892-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="88892-108">[out] Le tableau retourné <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` instances.</span><span class="sxs-lookup"><span data-stu-id="88892-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="88892-109">[out] Un pointeur vers un `ULONG` qui reçoit la taille de la `rgLocals` mémoire tampon requise pour contenir les variables locales.</span><span class="sxs-lookup"><span data-stu-id="88892-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88892-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="88892-110">Return Value</span></span>  
 <span data-ttu-id="88892-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="88892-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88892-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="88892-112">Requirements</span></span>  
 <span data-ttu-id="88892-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="88892-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88892-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88892-114">See Also</span></span>  
 [<span data-ttu-id="88892-115">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="88892-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
