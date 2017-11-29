---
title: "ISymUnmanagedWriter2::DefineLocalVariable2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 595cc3d8c503a5a6b2cbcb6665f7ff8aff5044d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="46083-102">ISymUnmanagedWriter2::DefineLocalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="46083-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="46083-103">Définit une variable unique dans la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="46083-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="46083-104">Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs dossiers de base dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="46083-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="46083-105">Dans ce cas, toutefois, les valeurs de la `startOffset` et `endOffset` paramètres ne doivent pas se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="46083-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46083-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46083-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46083-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46083-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="46083-108">[in] Le nom de variable locale.</span><span class="sxs-lookup"><span data-stu-id="46083-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="46083-109">[in] Attributs de la variables locale.</span><span class="sxs-lookup"><span data-stu-id="46083-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="46083-110">[in] Le jeton de métadonnées de la signature.</span><span class="sxs-lookup"><span data-stu-id="46083-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="46083-111">[in] Le type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="46083-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="46083-112">[in] La première adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="46083-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="46083-113">[in] La deuxième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="46083-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="46083-114">[in] Troisième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="46083-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="46083-115">[in] Offset de début de la variable.</span><span class="sxs-lookup"><span data-stu-id="46083-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="46083-116">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="46083-116">This parameter is optional.</span></span> <span data-ttu-id="46083-117">Si la valeur est 0, ce paramètre est ignoré et la variable est définie dans la portée entière.</span><span class="sxs-lookup"><span data-stu-id="46083-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="46083-118">Si elle est une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="46083-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="46083-119">[in] Offset de fin de la variable.</span><span class="sxs-lookup"><span data-stu-id="46083-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="46083-120">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="46083-120">This parameter is optional.</span></span> <span data-ttu-id="46083-121">Si la valeur est 0, ce paramètre est ignoré et la variable est définie dans la portée entière.</span><span class="sxs-lookup"><span data-stu-id="46083-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="46083-122">Si elle est une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="46083-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46083-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="46083-123">Return Value</span></span>  
 <span data-ttu-id="46083-124">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="46083-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46083-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46083-125">Requirements</span></span>  
 <span data-ttu-id="46083-126">**En-tête :** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="46083-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46083-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46083-127">See Also</span></span>  
 [<span data-ttu-id="46083-128">ISymUnmanagedWriter2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="46083-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="46083-129">DefineLocalVariable (méthode)</span><span class="sxs-lookup"><span data-stu-id="46083-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
