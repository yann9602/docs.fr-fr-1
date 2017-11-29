---
title: "ISymUnmanagedWriter::DefineParameter, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineParameter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 166087a27d0aa7b100da563c25f7e5a52612ce50
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="fd858-102">ISymUnmanagedWriter::DefineParameter, méthode</span><span class="sxs-lookup"><span data-stu-id="fd858-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="fd858-103">Définit un paramètre unique dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="fd858-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="fd858-104">Le type de paramètre provient de la position du paramètre (séquence) dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="fd858-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="fd858-105">Si les paramètres sont définis dans les métadonnées pour une méthode donnée, vous n’avez pas à les définir à nouveau à l’aide de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fd858-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="fd858-106">Les lecteurs de symbole doivent vérifier les métadonnées normales pour les paramètres avant de vérifier le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="fd858-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd858-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd858-107">Syntax</span></span>  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd858-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd858-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fd858-109">[in] Le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd858-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="fd858-110">[in] Les attributs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd858-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="fd858-111">[in] La signature de paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd858-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="fd858-112">[in] Le type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="fd858-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="fd858-113">[in] La première adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd858-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="fd858-114">[in] La deuxième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd858-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="fd858-115">[in] Troisième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="fd858-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd858-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fd858-116">Return Value</span></span>  
 <span data-ttu-id="fd858-117">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="fd858-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd858-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fd858-118">Requirements</span></span>  
 <span data-ttu-id="fd858-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd858-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd858-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd858-120">See Also</span></span>  
 [<span data-ttu-id="fd858-121">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="fd858-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
