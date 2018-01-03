---
title: "ISymUnmanagedReader::GetUserEntryPoint, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 328f44e797a49a899545fa43d940a3b0399ee8c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="a512e-102">ISymUnmanagedReader::GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="a512e-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="a512e-103">Retourne la méthode qui a été spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="a512e-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="a512e-104">Par exemple, cette méthode peut être méthode principale de l’utilisateur plutôt que des stubs générés par le compilateur avant la méthode principale.</span><span class="sxs-lookup"><span data-stu-id="a512e-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a512e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a512e-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a512e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a512e-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="a512e-107">[out] Pointeur vers une variable qui reçoit le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a512e-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a512e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a512e-108">Return Value</span></span>  
 <span data-ttu-id="a512e-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a512e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a512e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a512e-110">Requirements</span></span>  
 <span data-ttu-id="a512e-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a512e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a512e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a512e-112">See Also</span></span>  
 [<span data-ttu-id="a512e-113">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="a512e-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
