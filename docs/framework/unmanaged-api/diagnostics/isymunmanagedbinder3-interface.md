---
title: ISymUnmanagedBinder3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="07782-102">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="07782-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="07782-103">Étend l’interface du classeur de symboles.</span><span class="sxs-lookup"><span data-stu-id="07782-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="07782-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente le `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="07782-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07782-105">Il s’agit d’un risque de sécurité pour ouvrir un fichier du programme (PDB) de la base de données à partir d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="07782-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07782-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="07782-106">Methods</span></span>  
  
|<span data-ttu-id="07782-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="07782-107">Method</span></span>|<span data-ttu-id="07782-108">Description</span><span class="sxs-lookup"><span data-stu-id="07782-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07782-109">GetReaderFromCallback (méthode)</span><span class="sxs-lookup"><span data-stu-id="07782-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="07782-110">Permet à l’utilisateur d’implémenter ou de fournir via un rappel un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations de répertoire de débogage à partir de la mémoire</span><span class="sxs-lookup"><span data-stu-id="07782-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07782-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="07782-111">Requirements</span></span>  
 <span data-ttu-id="07782-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="07782-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07782-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07782-113">See Also</span></span>  
 [<span data-ttu-id="07782-114">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="07782-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="07782-115">ISymUnmanagedBinder (Interface)</span><span class="sxs-lookup"><span data-stu-id="07782-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="07782-116">ISymUnmanagedBinder2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="07782-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
