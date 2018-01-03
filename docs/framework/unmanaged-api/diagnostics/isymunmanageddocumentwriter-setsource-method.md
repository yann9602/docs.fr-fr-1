---
title: "ISymUnmanagedDocumentWriter::SetSource, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetSource
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287eba260ca20bae9da94ed2d00dcf1661fe14cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="dbe83-102">ISymUnmanagedDocumentWriter::SetSource, méthode</span><span class="sxs-lookup"><span data-stu-id="dbe83-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="dbe83-103">Définit la source pour un document qui est en cours d’écriture incorporée.</span><span class="sxs-lookup"><span data-stu-id="dbe83-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbe83-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbe83-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbe83-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="dbe83-106">[in] A `ULONG32` qui contient la taille de la `source` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="dbe83-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="dbe83-107">[in] Mémoire tampon qui stocke la source incorporée.</span><span class="sxs-lookup"><span data-stu-id="dbe83-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbe83-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dbe83-108">Return Value</span></span>  
 <span data-ttu-id="dbe83-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="dbe83-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe83-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dbe83-110">Requirements</span></span>  
 <span data-ttu-id="dbe83-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dbe83-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe83-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbe83-112">See Also</span></span>  
 [<span data-ttu-id="dbe83-113">ISymUnmanagedDocumentWriter, interface</span><span class="sxs-lookup"><span data-stu-id="dbe83-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
