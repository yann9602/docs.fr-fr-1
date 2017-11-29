---
title: "ISymUnmanagedWriter::OpenMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d63fb96635e34e07c3997c1aad838e67c70742
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="2f8c6-102">ISymUnmanagedWriter::OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="2f8c6-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="2f8c6-103">Ouvre une méthode dans le symbole des informations sont émises.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="2f8c6-104">La méthode donnée devient la méthode actuelle pour les appels à définir des points de séquence, les paramètres et les portées lexicales.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="2f8c6-105">Il existe une portée lexicale implicite autour de la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="2f8c6-106">Rouvrir une méthode qui a été précédemment fermée efface tous les symboles précédemment définis pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="2f8c6-107">Il peut être qu’une seule méthode ouverte à la fois.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8c6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f8c6-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f8c6-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f8c6-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="2f8c6-110">[in] Le jeton de métadonnées pour la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f8c6-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2f8c6-111">Return Value</span></span>  
 <span data-ttu-id="2f8c6-112">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2f8c6-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f8c6-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2f8c6-113">Requirements</span></span>  
 <span data-ttu-id="2f8c6-114">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2f8c6-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8c6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f8c6-115">See Also</span></span>  
 [<span data-ttu-id="2f8c6-116">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="2f8c6-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="2f8c6-117">CloseMethod (méthode)</span><span class="sxs-lookup"><span data-stu-id="2f8c6-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="2f8c6-118">OpenMethod2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="2f8c6-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
