---
title: "ISymUnmanagedWriter::SetUserEntryPoint, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da021bce46df02789547eb7ee50133b6f4d4af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="21793-102">ISymUnmanagedWriter::SetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="21793-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="21793-103">Spécifie la méthode définie par l’utilisateur qui est le point d’entrée pour ce module.</span><span class="sxs-lookup"><span data-stu-id="21793-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="21793-104">Par exemple, ce point d’entrée peut être méthode principale de l’utilisateur au lieu de stubs générés par le compilateur avant principal.</span><span class="sxs-lookup"><span data-stu-id="21793-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21793-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21793-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21793-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21793-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="21793-107">[in] Point de jeton de métadonnées de la méthode qui est l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="21793-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21793-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21793-108">Return Value</span></span>  
 <span data-ttu-id="21793-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="21793-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21793-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21793-110">Requirements</span></span>  
 <span data-ttu-id="21793-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="21793-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21793-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21793-112">See Also</span></span>  
 [<span data-ttu-id="21793-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="21793-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
