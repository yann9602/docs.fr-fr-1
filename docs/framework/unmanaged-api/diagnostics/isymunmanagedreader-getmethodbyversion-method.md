---
title: "ISymUnmanagedReader::GetMethodByVersion, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodByVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 810cc5cda9de7c61c1b23d1574ceff19bfec3bc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="f6021-102">ISymUnmanagedReader::GetMethodByVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="f6021-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="f6021-103">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et un numéro de version de la modifier et copier.</span><span class="sxs-lookup"><span data-stu-id="f6021-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="f6021-104">Numéros de version commencent à 1 et sont incrémentés à chaque fois que la méthode est modifiée à la suite d’une opération modifier et copier.</span><span class="sxs-lookup"><span data-stu-id="f6021-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6021-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6021-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6021-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6021-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="f6021-107">[in] Le jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="f6021-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="f6021-108">[in] La version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f6021-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f6021-109">[out] Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="f6021-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6021-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f6021-110">Return Value</span></span>  
 <span data-ttu-id="f6021-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f6021-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6021-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f6021-112">Requirements</span></span>  
 <span data-ttu-id="f6021-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f6021-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6021-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6021-114">See Also</span></span>  
 [<span data-ttu-id="f6021-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="f6021-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
