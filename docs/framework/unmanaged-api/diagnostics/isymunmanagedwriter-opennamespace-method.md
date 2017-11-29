---
title: "ISymUnmanagedWriter::OpenNamespace, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3dffd9605bd238446156d7a32e8e668ddd80916
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="eab29-102">ISymUnmanagedWriter::OpenNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="eab29-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="eab29-103">Ouvre un nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eab29-103">Opens a new namespace.</span></span> <span data-ttu-id="eab29-104">Appelez cette méthode avant de définir des méthodes ou variables qui occupent un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eab29-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="eab29-105">Espaces de noms peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="eab29-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab29-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eab29-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eab29-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eab29-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="eab29-108">[in] Pointeur vers le nom du nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eab29-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eab29-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eab29-109">Return Value</span></span>  
 <span data-ttu-id="eab29-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="eab29-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab29-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eab29-111">Requirements</span></span>  
 <span data-ttu-id="eab29-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eab29-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab29-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eab29-113">See Also</span></span>  
 [<span data-ttu-id="eab29-114">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="eab29-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="eab29-115">CloseNamespace (méthode)</span><span class="sxs-lookup"><span data-stu-id="eab29-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
