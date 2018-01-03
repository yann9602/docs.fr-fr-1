---
title: "ISymUnmanagedDocument::FindClosestLine, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.FindClosestLine
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5467f7d500719e8849b85a57195e98c6eeb7fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="f574f-102">ISymUnmanagedDocument::FindClosestLine, méthode</span><span class="sxs-lookup"><span data-stu-id="f574f-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="f574f-103">Retourne la ligne la plus proche qui est un point de séquence, en fonction d’une ligne dans ce document, qui peut être ou non un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="f574f-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f574f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f574f-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f574f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f574f-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="f574f-106">[in] Une ligne dans ce document.</span><span class="sxs-lookup"><span data-stu-id="f574f-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f574f-107">[out] Pointeur vers une variable qui reçoit la ligne.</span><span class="sxs-lookup"><span data-stu-id="f574f-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f574f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f574f-108">Return Value</span></span>  
 <span data-ttu-id="f574f-109">S_OK si la méthode réussit ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f574f-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f574f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f574f-110">See Also</span></span>  
 [<span data-ttu-id="f574f-111">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="f574f-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
