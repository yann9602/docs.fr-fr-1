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
ms.openlocfilehash: 08a89ba20b48c3d7faa3f3d27d4c57c55b33c355
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="59c18-102">ISymUnmanagedReader::GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="59c18-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="59c18-103">Retourne la méthode qui a été spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="59c18-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="59c18-104">Par exemple, cette méthode peut être méthode principale de l’utilisateur plutôt que des stubs générés par le compilateur avant la méthode principale.</span><span class="sxs-lookup"><span data-stu-id="59c18-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c18-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59c18-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59c18-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59c18-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="59c18-107">[out] Pointeur vers une variable qui reçoit le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="59c18-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59c18-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="59c18-108">Return Value</span></span>  
 <span data-ttu-id="59c18-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="59c18-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c18-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59c18-110">Requirements</span></span>  
 <span data-ttu-id="59c18-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59c18-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c18-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59c18-112">See Also</span></span>  
 [<span data-ttu-id="59c18-113">ISymUnmanagedReader (Interface)</span><span class="sxs-lookup"><span data-stu-id="59c18-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
