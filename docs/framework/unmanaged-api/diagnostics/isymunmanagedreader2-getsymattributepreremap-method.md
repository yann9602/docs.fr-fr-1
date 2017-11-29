---
title: "ISymUnmanagedReader2::GetSymAttributePreRemap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetSymAttributePreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75608d89b6fd34570166718de824150b0621c84e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="0f2b0-102">ISymUnmanagedReader2::GetSymAttributePreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="0f2b0-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="0f2b0-103">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="0f2b0-104">Contrairement aux attributs personnalisés des métadonnées, ces attributs sont conservés dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f2b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f2b0-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f2b0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f2b0-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="0f2b0-107">[in] Le jeton de métadonnées du parent.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="0f2b0-108">[in] Un pointeur vers un `WCHAR` qui contient le nom.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="0f2b0-109">[in] A `ULONG32` qui indique la taille de la `buffer` tableau.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="0f2b0-110">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les octets d’attributs.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0f2b0-111">[out] Pointeur vers la mémoire tampon qui reçoit les octets d’attributs.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f2b0-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0f2b0-112">Return Value</span></span>  
 <span data-ttu-id="0f2b0-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0f2b0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f2b0-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0f2b0-114">Requirements</span></span>  
 <span data-ttu-id="0f2b0-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0f2b0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2b0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f2b0-116">See Also</span></span>  
 [<span data-ttu-id="0f2b0-117">ISymUnmanagedReader2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f2b0-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
