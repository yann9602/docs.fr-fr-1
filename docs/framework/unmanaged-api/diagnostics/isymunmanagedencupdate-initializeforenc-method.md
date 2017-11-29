---
title: "ISymUnmanagedENCUpdate::InitializeForEnc, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.InitializeForEnc
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f42dc23c600739911dd04ec6c192544318e7849b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="32df4-102">ISymUnmanagedENCUpdate::InitializeForEnc, méthode</span><span class="sxs-lookup"><span data-stu-id="32df4-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>
<span data-ttu-id="32df4-103">Permet le calcul des limites de méthode avant le premier appel à la [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="32df4-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32df4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32df4-104">Syntax</span></span>  
  
```  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="32df4-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="32df4-105">Return Value</span></span>  
 <span data-ttu-id="32df4-106">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="32df4-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32df4-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="32df4-107">Requirements</span></span>  
 <span data-ttu-id="32df4-108">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32df4-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32df4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32df4-109">See Also</span></span>  
 [<span data-ttu-id="32df4-110">ISymUnmanagedENCUpdate (Interface)</span><span class="sxs-lookup"><span data-stu-id="32df4-110">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
