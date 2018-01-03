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
ms.workload: dotnet
ms.openlocfilehash: 7fe62a8f6b48d1a9931cc0310811d7fc42f7029b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="f7619-102">ISymUnmanagedWriter::DefineParameter, méthode</span><span class="sxs-lookup"><span data-stu-id="f7619-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="f7619-103">Définit un paramètre unique dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="f7619-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="f7619-104">Le type de paramètre provient de la position du paramètre (séquence) dans la signature de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f7619-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="f7619-105">Si les paramètres sont définis dans les métadonnées pour une méthode donnée, vous n’avez pas à les définir à nouveau à l’aide de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f7619-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="f7619-106">Les lecteurs de symbole doivent vérifier les métadonnées normales pour les paramètres avant de vérifier le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="f7619-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7619-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7619-107">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f7619-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7619-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f7619-109">[in] Le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f7619-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f7619-110">[in] Les attributs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f7619-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="f7619-111">[in] La signature de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f7619-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f7619-112">[in] Le type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="f7619-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f7619-113">[in] La première adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f7619-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f7619-114">[in] La deuxième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f7619-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f7619-115">[in] Troisième adresse de la spécification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f7619-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7619-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7619-116">Return Value</span></span>  
 <span data-ttu-id="f7619-117">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f7619-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7619-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7619-118">Requirements</span></span>  
 <span data-ttu-id="f7619-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f7619-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7619-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7619-120">See Also</span></span>  
 [<span data-ttu-id="f7619-121">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="f7619-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
