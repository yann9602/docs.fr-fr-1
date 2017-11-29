---
title: AssemblyAttributesGoHereM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHereM
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71fd6f0d998f190e203e415bdeca220e90cde579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="caca2-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="caca2-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="caca2-103">Utilisé par ALink en tant qu'espace réservé pour stocker des informations sur les attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="caca2-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caca2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caca2-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="caca2-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="caca2-105">Remarks</span></span>  
 <span data-ttu-id="caca2-106">Les références à ce type peuvent être incorporées dans les netmodules dont les sources contiennent des attributs personnalisés d'assembly.</span><span class="sxs-lookup"><span data-stu-id="caca2-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="caca2-107">Quand vous générez un manifeste d'assembly à partir d'un ou plusieurs netmodules qui contiennent des références à ces types, ALink utilise les informations associées à ces références pour émettre des attributs personnalisés réels.</span><span class="sxs-lookup"><span data-stu-id="caca2-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="caca2-108">Par conséquent, ce type n'est jamais instancié et ses références sont utilisées uniquement dans le cadre du processus de génération et n'ont aucune utilité dans l'assembly final.</span><span class="sxs-lookup"><span data-stu-id="caca2-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="caca2-109">Les références à ce type indiquent des attributs personnalisés qui ne sont pas liés à la sécurité et peuvent être utilisés plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="caca2-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="caca2-110">Ces types sont marqués comme étant « internes » dans le .NET Framework et se trouvent dans <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="caca2-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caca2-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="caca2-111">Requirements</span></span>  
 <span data-ttu-id="caca2-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="caca2-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caca2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caca2-113">See Also</span></span>  
 [<span data-ttu-id="caca2-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="caca2-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="caca2-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="caca2-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="caca2-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="caca2-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
