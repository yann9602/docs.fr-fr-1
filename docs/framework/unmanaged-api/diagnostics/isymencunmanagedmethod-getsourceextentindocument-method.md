---
title: "ISymENCUnmanagedMethod::GetSourceExtentInDocument, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6116ee89cb643cc0010ef2c8a463fa131777584e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="fe081-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="fe081-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="fe081-103">Obtient le plus petit de début ligne et la plus grande ligne de fin de la méthode dans un document spécifique.</span><span class="sxs-lookup"><span data-stu-id="fe081-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe081-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe081-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe081-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe081-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="fe081-106">[in] Pointeur vers le document.</span><span class="sxs-lookup"><span data-stu-id="fe081-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="fe081-107">[out] Un pointeur vers un `ULONG32` qui reçoit la ligne de début.</span><span class="sxs-lookup"><span data-stu-id="fe081-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="fe081-108">[out] Un pointeur vers un `ULONG32` qui reçoit la ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="fe081-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe081-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fe081-109">Return Value</span></span>  
 <span data-ttu-id="fe081-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="fe081-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe081-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fe081-111">Requirements</span></span>  
 <span data-ttu-id="fe081-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe081-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe081-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe081-113">See Also</span></span>  
 [<span data-ttu-id="fe081-114">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="fe081-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
