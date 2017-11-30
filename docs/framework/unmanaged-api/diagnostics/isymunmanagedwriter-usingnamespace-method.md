---
title: "ISymUnmanagedWriter::UsingNamespace, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.UsingNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9bfd5ca0c22a9b4da1acb1f93b29150beba865a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="c4a03-102">ISymUnmanagedWriter::UsingNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="c4a03-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="c4a03-103">Spécifie que le nom de l’espace de noms complet donné est utilisé dans la portée lexicale ouverte.</span><span class="sxs-lookup"><span data-stu-id="c4a03-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="c4a03-104">L’espace de noms sera utilisé dans toutes les portées qui héritent de la portée actuellement ouverte.</span><span class="sxs-lookup"><span data-stu-id="c4a03-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="c4a03-105">Fermeture de la portée actuelle s’arrête également l’utilisation de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4a03-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a03-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a03-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4a03-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4a03-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="c4a03-108">[in] Pointeur vers le nom qualifié complet de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4a03-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4a03-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c4a03-109">Return Value</span></span>  
 <span data-ttu-id="c4a03-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c4a03-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a03-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c4a03-111">Requirements</span></span>  
 <span data-ttu-id="c4a03-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c4a03-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a03-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4a03-113">See Also</span></span>  
 [<span data-ttu-id="c4a03-114">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="c4a03-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
