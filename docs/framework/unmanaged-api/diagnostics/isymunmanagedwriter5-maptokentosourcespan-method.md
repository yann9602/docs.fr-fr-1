---
title: "ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad40258b0fd562babb5e395ddbd05eca23e21ffe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="854e1-102">ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="854e1-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="854e1-103">Mappages s’étendre sur le jeton de métadonnées donné à la ligne source donné dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="854e1-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="854e1-104">Doit être appelé entre les appels à [openmaptokenstosourcespans, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et [closemaptokenstosourcespans, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="854e1-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854e1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="854e1-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="854e1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="854e1-106">Parameters</span></span>  
  
|<span data-ttu-id="854e1-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="854e1-107">Parameter</span></span>|<span data-ttu-id="854e1-108">Description</span><span class="sxs-lookup"><span data-stu-id="854e1-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="854e1-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="854e1-109">Return Value</span></span>  
 <span data-ttu-id="854e1-110">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="854e1-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854e1-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="854e1-111">Requirements</span></span>  
 <span data-ttu-id="854e1-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="854e1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854e1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="854e1-113">See Also</span></span>  
 [<span data-ttu-id="854e1-114">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="854e1-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
