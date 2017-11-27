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
ms.openlocfilehash: f7ab7f06ba280675ca8349500e766364d30f9349
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="41eef-102">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="41eef-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="41eef-103">Isymunmanagedwriter4, interface.</span><span class="sxs-lookup"><span data-stu-id="41eef-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41eef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41eef-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="41eef-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="41eef-105">Methods</span></span>  
 <span data-ttu-id="41eef-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="41eef-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="41eef-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="41eef-107">Method</span></span>|<span data-ttu-id="41eef-108">Description</span><span class="sxs-lookup"><span data-stu-id="41eef-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41eef-109">Getdebuginfowithpadding, méthode</span><span class="sxs-lookup"><span data-stu-id="41eef-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="41eef-110">Fonctionne comme [GetDebugInfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne de chemin d’accès est complétée avec des zéros qui suivent le caractère null de fin pour rendre les données de chaîne de taille fixe de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="41eef-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="41eef-111">Marge intérieure ne reçoit que si la longueur de chaîne de chemin d’accès lui-même est inférieure à `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="41eef-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="41eef-112">Cela rend plus facile d’écrire des outils que les fichiers PE de différence.</span><span class="sxs-lookup"><span data-stu-id="41eef-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41eef-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="41eef-113">Requirements</span></span>  
 <span data-ttu-id="41eef-114">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="41eef-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41eef-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41eef-115">See Also</span></span>  
 [<span data-ttu-id="41eef-116">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="41eef-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="41eef-117">ISymUnmanagedWriter3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="41eef-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
