---
title: "ISymUnmanagedWriter::DefineGlobalVariable, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineGlobalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7540dfcefbe7a331a26220a07b2e206c1302ddc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="2e715-102">ISymUnmanagedWriter::DefineGlobalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="2e715-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="2e715-103">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="2e715-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e715-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e715-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e715-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e715-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2e715-106">[in] Un pointeur vers un `WCHAR` qui définit le nom de la variable global.</span><span class="sxs-lookup"><span data-stu-id="2e715-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="2e715-107">[in] Attributs de la variable globales.</span><span class="sxs-lookup"><span data-stu-id="2e715-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="2e715-108">[in] A `ULONG32` qui indique la taille, en caractères, de la `signature` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="2e715-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="2e715-109">[in] La signature de variable globale.</span><span class="sxs-lookup"><span data-stu-id="2e715-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="2e715-110">[in] Le type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="2e715-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="2e715-111">[in] La première adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="2e715-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="2e715-112">[in] La deuxième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="2e715-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="2e715-113">[in] Troisième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="2e715-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e715-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2e715-114">Return Value</span></span>  
 <span data-ttu-id="2e715-115">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2e715-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e715-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2e715-116">Requirements</span></span>  
 <span data-ttu-id="2e715-117">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2e715-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e715-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e715-118">See Also</span></span>  
 [<span data-ttu-id="2e715-119">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="2e715-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="2e715-120">DefineLocalVariable (méthode)</span><span class="sxs-lookup"><span data-stu-id="2e715-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)  
 [<span data-ttu-id="2e715-121">DefineGlobalVariable2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="2e715-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
