---
title: "ISymENCUnmanagedMethod::GetDocumentsForMethodCount, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 804c760c22860aa3f9ded6c8a8fa9ad9b011e9a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="0f052-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount, méthode</span><span class="sxs-lookup"><span data-stu-id="0f052-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="0f052-103">Obtient le nombre de documents que cette méthode a des lignes.</span><span class="sxs-lookup"><span data-stu-id="0f052-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f052-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f052-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f052-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f052-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0f052-106">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les documents.</span><span class="sxs-lookup"><span data-stu-id="0f052-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f052-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0f052-107">Return Value</span></span>  
 <span data-ttu-id="0f052-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0f052-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f052-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f052-109">Requirements</span></span>  
 <span data-ttu-id="0f052-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0f052-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f052-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f052-111">See Also</span></span>  
 [<span data-ttu-id="0f052-112">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="0f052-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
