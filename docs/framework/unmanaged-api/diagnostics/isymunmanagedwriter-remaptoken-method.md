---
title: "ISymUnmanagedWriter::RemapToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.RemapToken
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d6c78a49c55bdc9093241952bee00ee331696e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="25c47-102">ISymUnmanagedWriter::RemapToken, méthode</span><span class="sxs-lookup"><span data-stu-id="25c47-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="25c47-103">Avertit le writer de symbole qu’un jeton de métadonnées a été remappé comme les métadonnées a été émises.</span><span class="sxs-lookup"><span data-stu-id="25c47-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="25c47-104">Si le writer de symbole a stocké l’ancien jeton dans le magasin de symboles, il doit soit mettre à jour que le jeton stocké avec la nouvelle valeur, soit enregistrer le mappage pour le lecteur de symboles correspondant à remapper pendant la phase de lecture.</span><span class="sxs-lookup"><span data-stu-id="25c47-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25c47-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25c47-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25c47-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25c47-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="25c47-107">[in] Le jeton de métadonnées qui a été remappé.</span><span class="sxs-lookup"><span data-stu-id="25c47-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="25c47-108">[in] Le nouveau jeton de métadonnées à laquelle `oldToken` a été remappée.</span><span class="sxs-lookup"><span data-stu-id="25c47-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25c47-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="25c47-109">Return Value</span></span>  
 <span data-ttu-id="25c47-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="25c47-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25c47-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="25c47-111">Requirements</span></span>  
 <span data-ttu-id="25c47-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25c47-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c47-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25c47-113">See Also</span></span>  
 [<span data-ttu-id="25c47-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="25c47-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
