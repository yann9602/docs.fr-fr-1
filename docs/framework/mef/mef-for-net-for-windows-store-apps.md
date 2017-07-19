---
title: "Espaces de noms MEF pour .NET pour les applications Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: 3
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 3
---
# Espaces de noms MEF pour .NET pour les applications Windows Store
<xref:System.Composition?displayProperty=fullName> et ses espaces de noms enfants contiennent des types pour le développement des applications du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] extensibles à l'aide de Managed Extensibility Framework \(MEF\).  Ces espaces de noms font partie du sous\-ensemble [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] pour le système d'exploitation [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 Ces espaces de noms ne font pas partie de la principale bibliothèque de classes distribuée avec le .NET Framework.  Pour installer ces espaces de noms, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Manage NuGet Packages** dans le menu **Projet** et recherchez en ligne le package Microsoft.Composition.  
  
-   <xref:System.Composition?displayProperty=fullName> fournit des classes qui constituent le cœur de MEF pour les applications du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
-   <xref:System.Composition.Convention?displayProperty=fullName> fournit des types qui prennent en charge l'utilisation de MEF avec un modèle de configuration conventionnel.  
  
-   <xref:System.Composition.Hosting?displayProperty=fullName> fournit des types MEF qui sont utiles aux développeurs d'applications hôtes.  
  
-   <xref:System.Composition.Hosting.Core?displayProperty=fullName> fournit des types MEF utilisés en interne par le moteur de composition.  
  
 Pour plus d'informations sur [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] et une liste des espaces de noms et des types qu'ils contiennent, consultez [.NET framework pour windows stockent la présentation d'applications](http://go.microsoft.com/fwlink/p/?LinkID=238312) au centre de dev windows.  
  
## Voir aussi  
 [Vue d'ensemble de l'utilisation de .NET pour les applications Windows Store](http://go.microsoft.com/fwlink/p/?LinkID=238312)   
 [.NET pour les applications Windows Store – API prises en charge](http://go.microsoft.com/fwlink/p/?LinkID=247912)   
 [Managed Extensibility Framework \(MEF\)](../../../docs/framework/mef/index.md)