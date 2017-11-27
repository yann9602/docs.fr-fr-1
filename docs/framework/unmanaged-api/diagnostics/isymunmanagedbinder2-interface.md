---
title: ISymUnmanagedBinder2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2 Interface
helpviewer_keywords: ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c276f0abedf4ccab92770af649a8dd0afb6d39d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="71c7e-102">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="71c7e-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="71c7e-103">Représente un classeur de symboles pour le code non managé et étend la [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="71c7e-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71c7e-104">Il s’agit d’un risque de sécurité pour ouvrir un fichier du programme (PDB) de la base de données à partir d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="71c7e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71c7e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="71c7e-105">Methods</span></span>  
  
|<span data-ttu-id="71c7e-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="71c7e-106">Method</span></span>|<span data-ttu-id="71c7e-107">Description</span><span class="sxs-lookup"><span data-stu-id="71c7e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71c7e-108">GetReaderForFile2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="71c7e-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="71c7e-109">Une interface de métadonnées et un nom de fichier, retourne le correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface qui lit les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="71c7e-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="71c7e-110">Fournit une recherche plus étendue que le [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="71c7e-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71c7e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="71c7e-111">Requirements</span></span>  
 <span data-ttu-id="71c7e-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="71c7e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c7e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71c7e-113">See Also</span></span>  
 [<span data-ttu-id="71c7e-114">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="71c7e-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="71c7e-115">ISymUnmanagedBinder (Interface)</span><span class="sxs-lookup"><span data-stu-id="71c7e-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="71c7e-116">ISymUnmanagedBinder3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="71c7e-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
