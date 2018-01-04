---
title: "ISymUnmanagedDocument::GetLanguage, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguage
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31fdd2caaf877372fa28693cdc5b09ddf601427c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="51621-102">ISymUnmanagedDocument::GetLanguage, méthode</span><span class="sxs-lookup"><span data-stu-id="51621-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="51621-103">Obtient l’identificateur de langue de ce document</span><span class="sxs-lookup"><span data-stu-id="51621-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51621-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51621-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51621-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51621-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="51621-106">[out] Pointeur vers une variable qui reçoit l’identificateur de langue.</span><span class="sxs-lookup"><span data-stu-id="51621-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51621-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="51621-107">Return Value</span></span>  
 <span data-ttu-id="51621-108">S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="51621-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51621-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51621-109">See Also</span></span>  
 [<span data-ttu-id="51621-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="51621-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
