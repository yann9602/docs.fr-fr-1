---
title: ISymUnmanagedWriter4, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5531b491da70cb78de1234e750c2e15390c10ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="a8f44-102">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="a8f44-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="a8f44-103">Isymunmanagedwriter4, interface.</span><span class="sxs-lookup"><span data-stu-id="a8f44-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8f44-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="a8f44-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a8f44-105">Methods</span></span>  
 <span data-ttu-id="a8f44-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8f44-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="a8f44-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="a8f44-107">Method</span></span>|<span data-ttu-id="a8f44-108">Description</span><span class="sxs-lookup"><span data-stu-id="a8f44-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8f44-109">GetDebugInfoWithPadding, méthode</span><span class="sxs-lookup"><span data-stu-id="a8f44-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="a8f44-110">Fonctionne comme [GetDebugInfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne de chemin d’accès est complétée avec des zéros qui suivent le caractère null de fin pour rendre les données de chaîne de taille fixe de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="a8f44-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="a8f44-111">Marge intérieure ne reçoit que si la longueur de chaîne de chemin d’accès lui-même est inférieure à `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="a8f44-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="a8f44-112">Cela rend plus facile d’écrire des outils que les fichiers PE de différence.</span><span class="sxs-lookup"><span data-stu-id="a8f44-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8f44-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8f44-113">Requirements</span></span>  
 <span data-ttu-id="a8f44-114">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a8f44-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f44-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8f44-115">See Also</span></span>  
 [<span data-ttu-id="a8f44-116">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="a8f44-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="a8f44-117">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="a8f44-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
