---
title: Interface de ICorProfilerInfo7
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85bf82a01f431e42a5714eeb54e17a34314534
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="27889-102">Interface de ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="27889-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="27889-103">[Prise en charge dans [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="27889-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="27889-104">Une sous-classe de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) qui fournit une méthode à appliquer qui vient d’être défini des métadonnées à un module et qui fournit l’accès à un flux de symbole de mémoire.</span><span class="sxs-lookup"><span data-stu-id="27889-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27889-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="27889-105">Methods</span></span>  
  
|<span data-ttu-id="27889-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="27889-106">Method</span></span>|<span data-ttu-id="27889-107">Description</span><span class="sxs-lookup"><span data-stu-id="27889-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27889-108">ApplyMetaData (méthode)</span><span class="sxs-lookup"><span data-stu-id="27889-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="27889-109">Applique les métadonnées qui vient d’être définie par le `IMetadataEmit::Define*` méthodes à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="27889-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="27889-110">GetInMemorySymbolsLength (méthode)</span><span class="sxs-lookup"><span data-stu-id="27889-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="27889-111">Retourne la longueur d’un flux de symbole de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="27889-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="27889-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="27889-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="27889-113">Lit les octets à partir d’un flux de symbole de mémoire.</span><span class="sxs-lookup"><span data-stu-id="27889-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27889-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="27889-114">Requirements</span></span>  
 <span data-ttu-id="27889-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27889-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27889-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27889-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27889-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27889-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27889-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27889-118">See Also</span></span>  
 [<span data-ttu-id="27889-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="27889-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
