---
title: "ISymUnmanagedNamespace::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b29e71a9a1185a7080f71b1621a07dd7ae41a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="de16b-102">ISymUnmanagedNamespace::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="de16b-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="de16b-103">Obtient le nom de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="de16b-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de16b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de16b-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de16b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de16b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="de16b-106">[in] A `ULONG32` qui indique la taille de la `szName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="de16b-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="de16b-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom de l’espace de noms, y compris le caractère null de fin.</span><span class="sxs-lookup"><span data-stu-id="de16b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="de16b-108">[out] Pointeur vers une mémoire tampon qui contient le nom de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="de16b-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de16b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="de16b-109">Return Value</span></span>  
 <span data-ttu-id="de16b-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="de16b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de16b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="de16b-111">Requirements</span></span>  
 <span data-ttu-id="de16b-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="de16b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de16b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de16b-113">See Also</span></span>  
 [<span data-ttu-id="de16b-114">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="de16b-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
