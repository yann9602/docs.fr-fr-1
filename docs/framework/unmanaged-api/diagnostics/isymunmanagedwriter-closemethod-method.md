---
title: "ISymUnmanagedWriter::CloseMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21c4cdd42613f5e8b60c39426b4f169a034ce7a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="0d876-102">ISymUnmanagedWriter::CloseMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="0d876-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="0d876-103">Ferme la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="0d876-103">Closes the current method.</span></span> <span data-ttu-id="0d876-104">Une fois qu’une méthode est fermée, plus aucun symbole ne peut être définie qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="0d876-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d876-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d876-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0d876-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0d876-106">Return Value</span></span>  
 <span data-ttu-id="0d876-107">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0d876-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d876-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d876-108">Requirements</span></span>  
 <span data-ttu-id="0d876-109">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0d876-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d876-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d876-110">See Also</span></span>  
 [<span data-ttu-id="0d876-111">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="0d876-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="0d876-112">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="0d876-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
