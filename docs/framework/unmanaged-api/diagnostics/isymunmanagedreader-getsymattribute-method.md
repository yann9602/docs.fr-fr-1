---
title: "ISymUnmanagedReader::GetSymAttribute, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f57d2c4541945d90b1695850311928884fdc9cc5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="2edca-102">ISymUnmanagedReader::GetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="2edca-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="2edca-103">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="2edca-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="2edca-104">Contrairement aux attributs personnalisés des métadonnées, ces attributs personnalisés sont conservés dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="2edca-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2edca-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2edca-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2edca-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="2edca-107">[in] Le jeton de métadonnées pour l’objet pour lequel l’attribut est demandé.</span><span class="sxs-lookup"><span data-stu-id="2edca-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="2edca-108">[in] Pointeur vers la variable qui indique l’attribut à récupérer.</span><span class="sxs-lookup"><span data-stu-id="2edca-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="2edca-109">[in] Taille du tableau `buffer`.</span><span class="sxs-lookup"><span data-stu-id="2edca-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="2edca-110">[out] Pointeur vers la variable qui reçoit la longueur des données d’attribut.</span><span class="sxs-lookup"><span data-stu-id="2edca-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="2edca-111">[out] Pointeur vers la variable qui reçoit les données d’attribut.</span><span class="sxs-lookup"><span data-stu-id="2edca-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2edca-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2edca-112">Return Value</span></span>  
 <span data-ttu-id="2edca-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur...</span><span class="sxs-lookup"><span data-stu-id="2edca-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2edca-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2edca-114">Requirements</span></span>  
 <span data-ttu-id="2edca-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2edca-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edca-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2edca-116">See Also</span></span>  
 [<span data-ttu-id="2edca-117">ISymUnmanagedReader (Interface)</span><span class="sxs-lookup"><span data-stu-id="2edca-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
