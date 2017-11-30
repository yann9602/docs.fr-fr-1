---
title: "ISymUnmanagedWriter3::Commit, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.Commit
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3ff2baa8a5006e2a3a83ddbcf5ca79b78350794b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="361d6-102">ISymUnmanagedWriter3::Commit, méthode</span><span class="sxs-lookup"><span data-stu-id="361d6-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="361d6-103">Valide les modifications écrites jusqu'à présent dans le flux de données.</span><span class="sxs-lookup"><span data-stu-id="361d6-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="361d6-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="361d6-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="361d6-105">Return Value</span></span>  
 <span data-ttu-id="361d6-106">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="361d6-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="361d6-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="361d6-107">Requirements</span></span>  
 <span data-ttu-id="361d6-108">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="361d6-108">**Header:** CorSym.idl , CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="361d6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="361d6-109">See Also</span></span>  
 [<span data-ttu-id="361d6-110">ISymUnmanagedWriter3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="361d6-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
