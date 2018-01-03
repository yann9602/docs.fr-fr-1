---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85486370d567ceb1506c41f6aa7c4f3a1929941
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="0ef8f-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode</span><span class="sxs-lookup"><span data-stu-id="0ef8f-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="0ef8f-103">Fonctionne comme [GetDebugInfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne de chemin d’accès est complétée avec des zéros qui suivent le caractère null de fin pour rendre les données de chaîne de taille fixe de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0ef8f-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="0ef8f-104">Marge intérieure ne reçoit que si la longueur de chaîne de chemin d’accès lui-même est inférieure à `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0ef8f-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="0ef8f-105">Cela rend plus facile d’écrire des outils que les fichiers PE de différence.</span><span class="sxs-lookup"><span data-stu-id="0ef8f-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ef8f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ef8f-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ef8f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0ef8f-107">Parameters</span></span>  
  
|<span data-ttu-id="0ef8f-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="0ef8f-108">Parameter</span></span>|<span data-ttu-id="0ef8f-109">Description</span><span class="sxs-lookup"><span data-stu-id="0ef8f-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="0ef8f-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0ef8f-110">Return Value</span></span>  
 <span data-ttu-id="0ef8f-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0ef8f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ef8f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0ef8f-112">Requirements</span></span>  
 <span data-ttu-id="0ef8f-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0ef8f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef8f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ef8f-114">See Also</span></span>  
 [<span data-ttu-id="0ef8f-115">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="0ef8f-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
