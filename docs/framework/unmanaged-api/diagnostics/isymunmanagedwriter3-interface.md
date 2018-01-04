---
title: ISymUnmanagedWriter3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3
helpviewer_keywords: ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49928044bcf2c598cdc0e4315d569f2c4eb02f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="b1a5a-102">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="b1a5a-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="b1a5a-103">Représente un writer de symbole et fournit des méthodes pour définir des documents, les points de séquence, les portées lexicales et variables.</span><span class="sxs-lookup"><span data-stu-id="b1a5a-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b1a5a-104">Cette interface étend la [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b1a5a-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1a5a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b1a5a-105">Methods</span></span>  
  
|<span data-ttu-id="b1a5a-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="b1a5a-106">Method</span></span>|<span data-ttu-id="b1a5a-107">Description</span><span class="sxs-lookup"><span data-stu-id="b1a5a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1a5a-108">Commit, méthode</span><span class="sxs-lookup"><span data-stu-id="b1a5a-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="b1a5a-109">Valide les modifications écrites jusqu'à présent dans le flux de données.</span><span class="sxs-lookup"><span data-stu-id="b1a5a-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="b1a5a-110">OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="b1a5a-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="b1a5a-111">Ouvre une méthode et fournit sa vraie section compensée dans l’image.</span><span class="sxs-lookup"><span data-stu-id="b1a5a-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1a5a-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b1a5a-112">Requirements</span></span>  
 <span data-ttu-id="b1a5a-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b1a5a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a5a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1a5a-114">See Also</span></span>  
 [<span data-ttu-id="b1a5a-115">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="b1a5a-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b1a5a-116">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="b1a5a-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b1a5a-117">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="b1a5a-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
