---
title: ISymUnmanagedBinder, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="84659-102">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="84659-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="84659-103">Représente un classeur de symboles pour le code non managé.</span><span class="sxs-lookup"><span data-stu-id="84659-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84659-104">Il s’agit d’un risque de sécurité pour ouvrir un fichier du programme (PDB) de la base de données à partir d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="84659-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84659-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="84659-105">Methods</span></span>  
  
|<span data-ttu-id="84659-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="84659-106">Method</span></span>|<span data-ttu-id="84659-107">Description</span><span class="sxs-lookup"><span data-stu-id="84659-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84659-108">GetReaderForFile (méthode)</span><span class="sxs-lookup"><span data-stu-id="84659-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="84659-109">Une interface de métadonnées et un nom de fichier, retourne le correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure qui lit les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="84659-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="84659-110">GetReaderFromStream (méthode)</span><span class="sxs-lookup"><span data-stu-id="84659-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="84659-111">Une interface de métadonnées et un flux qui contient le magasin de symboles, retourne le correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> symboles de structure qui lira le débogage à partir du magasin de symboles donné.</span><span class="sxs-lookup"><span data-stu-id="84659-111">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84659-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="84659-112">Requirements</span></span>  
 <span data-ttu-id="84659-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="84659-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84659-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84659-114">See Also</span></span>  
 [<span data-ttu-id="84659-115">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="84659-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="84659-116">ISymUnmanagedBinder2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="84659-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="84659-117">ISymUnmanagedBinder3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="84659-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
