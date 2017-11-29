---
title: "ISymUnmanagedReader::GetNamespaces, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c4404977fab42fb46292440473cd30f6cb162d6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="c4d7e-102">ISymUnmanagedReader::GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="c4d7e-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="c4d7e-103">Obtient les espaces de noms définis dans une portée globale dans ce magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="c4d7e-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4d7e-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4d7e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4d7e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="c4d7e-106">[in] La taille du tableau d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="c4d7e-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="c4d7e-107">[out] Pointeur vers une variable qui reçoit la longueur de la liste de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4d7e-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="c4d7e-108">[out] Pointeur vers une variable qui reçoit la liste de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4d7e-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4d7e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c4d7e-109">Return Value</span></span>  
 <span data-ttu-id="c4d7e-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c4d7e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d7e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c4d7e-111">Requirements</span></span>  
 <span data-ttu-id="c4d7e-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c4d7e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d7e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4d7e-113">See Also</span></span>  
 [<span data-ttu-id="c4d7e-114">ISymUnmanagedReader (Interface)</span><span class="sxs-lookup"><span data-stu-id="c4d7e-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
