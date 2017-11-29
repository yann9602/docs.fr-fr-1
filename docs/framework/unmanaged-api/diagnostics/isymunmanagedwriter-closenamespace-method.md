---
title: "ISymUnmanagedWriter::CloseNamespace, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8423e21fbc868e4b6891279d19b2be7c1faef583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="b6ab1-102">ISymUnmanagedWriter::CloseNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="b6ab1-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="b6ab1-103">Espace de noms le plus récemment ouvert par se ferme.</span><span class="sxs-lookup"><span data-stu-id="b6ab1-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ab1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ab1-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b6ab1-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6ab1-105">Return Value</span></span>  
 <span data-ttu-id="b6ab1-106">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b6ab1-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ab1-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b6ab1-107">Requirements</span></span>  
 <span data-ttu-id="b6ab1-108">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b6ab1-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ab1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6ab1-109">See Also</span></span>  
 [<span data-ttu-id="b6ab1-110">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="b6ab1-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b6ab1-111">OpenNamespace (méthode)</span><span class="sxs-lookup"><span data-stu-id="b6ab1-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
