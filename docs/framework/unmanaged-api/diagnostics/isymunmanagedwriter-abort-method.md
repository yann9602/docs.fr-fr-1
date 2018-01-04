---
title: "ISymUnmanagedWriter::Abort, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Abort
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8013bf2118a73a8b5eb8a5b160f2655a83382efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="9c4c3-102">ISymUnmanagedWriter::Abort, méthode</span><span class="sxs-lookup"><span data-stu-id="9c4c3-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="9c4c3-103">Ferme le writer de symbole sans valider les symboles dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="9c4c3-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="9c4c3-104">Après cet appel, le writer de symbole devient non valide pour les autres mises à jour.</span><span class="sxs-lookup"><span data-stu-id="9c4c3-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="9c4c3-105">Pour valider les symboles et fermer le writer de symbole, utilisez le [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="9c4c3-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c4c3-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9c4c3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9c4c3-107">Return Value</span></span>  
 <span data-ttu-id="9c4c3-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9c4c3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c4c3-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9c4c3-109">Requirements</span></span>  
 <span data-ttu-id="9c4c3-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9c4c3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4c3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c4c3-111">See Also</span></span>  
 [<span data-ttu-id="9c4c3-112">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="9c4c3-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
