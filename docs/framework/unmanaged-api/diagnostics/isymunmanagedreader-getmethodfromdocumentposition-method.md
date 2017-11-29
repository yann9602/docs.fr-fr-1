---
title: "ISymUnmanagedReader::GetMethodFromDocumentPosition, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad64d5722df68859e7be9d44b94b95cf1f43823f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="71c97-102">ISymUnmanagedReader::GetMethodFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="71c97-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="71c97-103">Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="71c97-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71c97-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71c97-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="71c97-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="71c97-106">[in] Le document spécifié.</span><span class="sxs-lookup"><span data-stu-id="71c97-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="71c97-107">[in] La ligne du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="71c97-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="71c97-108">[in] La colonne du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="71c97-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="71c97-109">[out] Un pointeur vers l’adresse d’un [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objet qui représente la méthode qui contient le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="71c97-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71c97-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="71c97-110">Return Value</span></span>  
 <span data-ttu-id="71c97-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="71c97-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71c97-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="71c97-112">Requirements</span></span>  
 <span data-ttu-id="71c97-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="71c97-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c97-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71c97-114">See Also</span></span>  
 [<span data-ttu-id="71c97-115">ISymUnmanagedReader (Interface)</span><span class="sxs-lookup"><span data-stu-id="71c97-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
