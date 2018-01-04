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
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Fonctions d'assistance de Tlbexp (Informations de référence sur les API non managées)
Le [outil Type Library Exporter](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) charge une bibliothèque de liens dynamiques nommée TlbRef.dll. Cette DLL contient deux fonctions d’assistance et une interface que l’outil exportateur utilise pendant le processus de conversion de l’assembly de bibliothèque de types.  
  
## <a name="in-this-section"></a>Dans cette section  
 [GetTypeLibInfo, fonction](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 Fournit des informations de localisation et de système d’exploitation pour une bibliothèque de types.  
  
 [LoadTypeLibWithResolver, fonction](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 Charge une bibliothèque de types à l’aide d’une implémentation de la [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) pour résoudre toute référence les bibliothèques de types.  
  
 [ITypeLibResolver, interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 Fournit la [ResolveTypeLib, méthode](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), qui retourne le chemin d’accès qualifié complet d’une bibliothèque de types.
