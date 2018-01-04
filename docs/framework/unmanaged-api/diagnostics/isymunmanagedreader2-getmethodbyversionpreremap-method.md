---
title: "ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0745428c6e9a51c5c7fa413838cf65eb907eea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="4e9ba-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="4e9ba-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="4e9ba-103">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et un numéro de version modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="4e9ba-104">Numéros de version commencent à 1 et sont incrémentés à chaque fois que la méthode est modifiée à la suite d’une opération modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e9ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e9ba-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e9ba-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e9ba-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="4e9ba-107">[in] Le jeton de métadonnées de méthode.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="4e9ba-108">[in] La version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4e9ba-109">[out] Un pointeur vers retourné [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e9ba-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4e9ba-110">Return Value</span></span>  
 <span data-ttu-id="4e9ba-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e9ba-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4e9ba-112">Requirements</span></span>  
 <span data-ttu-id="4e9ba-113">**En-tête :** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="4e9ba-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="4e9ba-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4e9ba-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9ba-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e9ba-115">See Also</span></span>  
 [<span data-ttu-id="4e9ba-116">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="4e9ba-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
