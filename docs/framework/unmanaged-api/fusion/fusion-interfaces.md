---
title: Interfaces de fusion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1742025bed977dfd377a78db42df42c1bc43966
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-interfaces"></a>Interfaces de fusion
Cette section décrit les interfaces non managées que l’API de fusion utilise pour accéder aux propriétés des ressources d’une application et pour localiser les versions correctes de ces ressources pour l’application.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IAppIdAuthority (Interface)](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 Fournit des méthodes qui génèrent et comparer les clés pour les identités d’application et les références.  
  
 [IAssemblyCache (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 Fournit une représentation du global assembly cache.  
  
 [IAssemblyCacheItem (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 Représente un seul assembly dans le global assembly cache.  
  
 [IAssemblyEnum (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 Représente un énumérateur pour un tableau de `IAssemblyName` objets.  
  
 [IAssemblyName (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 Fournit des méthodes pour décrire et travailler avec l’identité unique d’un assembly.  
  
 [IDefinitionAppId (Interface)](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 Représente un identificateur unique pour le code qui définit l’application dans la portée actuelle.  
  
 [IDefinitionIdentity (Interface)](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 Représente la signature unique du code qui définit l’application dans la portée actuelle.  
  
 [IEnumDefinitionIdentity (Interface)](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 Sert d’énumérateur pour une collection de `IDefinitionIdentity` objets.  
  
 [IEnumIDENTITY_ATTRIBUTE (Interface)](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 Sert d’énumérateur pour les attributs de l’objet de code dans la portée actuelle.  
  
 [IEnumReferenceIdentity (Interface)](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 Sert d’énumérateur pour une collection de `IReferenceIdentity` objets.  
  
 [IIdentityAuthority (Interface)](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 Gère les clés d’identité pour les objets de code.  
  
 [IInstallReferenceEnum (Interface)](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 Représente un énumérateur pour les assemblys référencés installés dans le global assembly cache.  
  
 [IInstallReferenceItem (Interface)](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 Représente un élément installé dans le global assembly cache.  
  
 [IReferenceAppId (Interface)](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 Représente une référence à l’identificateur unique pour l’application dans la portée actuelle.  
  
 [IReferenceIdentity (Interface)](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 Représente une référence à la signature unique d’un objet de code.  
  
## <a name="reference"></a>Référence  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [Énumérations de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Structures de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
