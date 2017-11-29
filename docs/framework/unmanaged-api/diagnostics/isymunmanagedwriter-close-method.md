---
title: "ISymUnmanagedWriter::Close, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Close
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad0cec59531a7e22d0a4d2220cb2dfcdd8f27596
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="df0e0-102">ISymUnmanagedWriter::Close, méthode</span><span class="sxs-lookup"><span data-stu-id="df0e0-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="df0e0-103">Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="df0e0-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df0e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df0e0-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="df0e0-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="df0e0-105">Return Value</span></span>  
 <span data-ttu-id="df0e0-106">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="df0e0-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df0e0-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="df0e0-107">Remarks</span></span>  
 <span data-ttu-id="df0e0-108">Après cet appel, le writer de symbole devient non valide pour les autres mises à jour.</span><span class="sxs-lookup"><span data-stu-id="df0e0-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="df0e0-109">Pour fermer le writer de symbole sans valider les symboles, utilisez le [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="df0e0-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df0e0-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="df0e0-110">Requirements</span></span>  
 <span data-ttu-id="df0e0-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df0e0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df0e0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df0e0-112">See Also</span></span>  
 [<span data-ttu-id="df0e0-113">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="df0e0-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
