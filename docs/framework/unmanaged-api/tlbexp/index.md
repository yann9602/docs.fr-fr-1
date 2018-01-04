---
title: "Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a9d483e101fdb94a43055b6081fcc31a458a1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="24bb9-102">Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="24bb9-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="24bb9-103">Le [outil Type Library Exporter](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) charge une bibliothèque de liens dynamiques nommée TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="24bb9-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="24bb9-104">Cette DLL contient deux fonctions d’assistance et une interface que l’outil exportateur utilise pendant le processus de conversion de l’assembly de bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="24bb9-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24bb9-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="24bb9-105">In This Section</span></span>  
 [<span data-ttu-id="24bb9-106">GetTypeLibInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="24bb9-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="24bb9-107">Fournit des informations de localisation et de système d’exploitation pour une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="24bb9-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="24bb9-108">LoadTypeLibWithResolver, fonction</span><span class="sxs-lookup"><span data-stu-id="24bb9-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="24bb9-109">Charge une bibliothèque de types à l’aide d’une implémentation de la [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) pour résoudre toute référence les bibliothèques de types.</span><span class="sxs-lookup"><span data-stu-id="24bb9-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="24bb9-110">ITypeLibResolver, interface</span><span class="sxs-lookup"><span data-stu-id="24bb9-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="24bb9-111">Fournit la [ResolveTypeLib, méthode](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), qui retourne le chemin d’accès qualifié complet d’une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="24bb9-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
