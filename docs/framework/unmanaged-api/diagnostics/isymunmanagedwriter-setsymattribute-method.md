---
title: "ISymUnmanagedWriter::SetSymAttribute, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90360d6fe5a1a95719a9bb09e5e0b6b2a70675a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="89058-102">ISymUnmanagedWriter::SetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="89058-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="89058-103">Définit un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="89058-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="89058-104">Ces attributs sont conservés dans le magasin de symboles, contrairement aux attributs personnalisés des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="89058-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89058-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89058-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89058-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89058-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="89058-107">[in] Le jeton de métadonnées pour lequel l’attribut est défini.</span><span class="sxs-lookup"><span data-stu-id="89058-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="89058-108">[in] Un pointeur vers un `WCHAR` qui contient le nom d’attribut.</span><span class="sxs-lookup"><span data-stu-id="89058-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="89058-109">[in] A `ULONG32` qui indique la taille de la `data` tableau.</span><span class="sxs-lookup"><span data-stu-id="89058-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="89058-110">[in] La valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="89058-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89058-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="89058-111">Return Value</span></span>  
 <span data-ttu-id="89058-112">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="89058-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89058-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="89058-113">Requirements</span></span>  
 <span data-ttu-id="89058-114">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="89058-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89058-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89058-115">See Also</span></span>  
 [<span data-ttu-id="89058-116">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="89058-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
