---
title: "Ex&#233;cution d&#39;applications intranet de confiance totale | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "confiance totale, exécuter des applications intranet en"
  - "applications intranet, exécuter en mode confiance totale"
  - "exécuter des applications intranet en mode confiance totale"
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# Ex&#233;cution d&#39;applications intranet de confiance totale
À partir du .NET Framework version 3.5 Service Pack 1 \(SP1\), les applications et leurs assemblys de bibliothèque peuvent être exécutés comme des assemblys de confiance totale à partir d'un partage réseau.  La preuve de zone <xref:System.Security.SecurityZone> est ajoutée automatiquement aux assemblys chargés sur l'intranet à partir d'un partage.  Cette preuve fournit à ces assemblys le même jeu accordé \(qui est généralement de confiance totale\) qu'aux assemblys qui résident sur l'ordinateur.  Cette fonctionnalité ne s'applique pas aux applications ClickOnce ou aux applications qui doivent être exécutées sur un hôte.  
  
## Règles relatives aux assemblys de bibliothèque  
 Les règles suivantes s'appliquent aux assemblys qui sont chargés par un exécutable sur un partage réseau :  
  
-   Les assemblys de bibliothèque doivent résider dans le même dossier que l'assembly exécutable.  Les assemblys qui résident dans un sous\-dossier ou qui sont référencés à un autre chemin d'accès ne se voient pas accorder une confiance totale.  
  
-   Si l'exécutable charge un assembly en différé, il doit utiliser le même chemin que pour le lancement de l'exécutable.  Par exemple, si le partage \\\\*network\-computer*\\*share* est associé à une lettre de lecteur et si l'exécutable est lancé depuis ce chemin, les assemblys chargés par l'exécutable depuis le chemin réseau ne se verront pas accorder une confiance totale.  Pour charger un assembly en différé dans la zone <xref:System.Security.SecurityZone>, l'exécutable doit utiliser le chemin d'accès du lecteur.  
  
## Restauration de l'ancienne stratégie d'intranet  
 Dans les versions antérieures du .NET Framework, une preuve de zone <xref:System.Security.SecurityZone> était accordée aux assemblys partagés.  Vous deviez spécifier la stratégie de sécurité d'accès du code pour accorder une confiance totale à un assembly sur un partage.  
  
 Ce nouveau comportement est le comportement par défaut pour les assemblys intranet.  Vous pouvez revenir au comportement antérieur qui consiste à fournir une preuve <xref:System.Security.SecurityZone> en définissant une clé de Registre qui s'applique à toutes les applications de l'ordinateur.  Le processus diffère pour les ordinateurs 32 bits et 64 bits.  
  
-   Sur les ordinateurs 32 bits, créez une sous\-clé sous la clé HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework dans la base de registres.  Utilisez le nom de clé LegacyMyComputerZone avec une valeur DWORD égale à 1.  
  
-   Sur les ordinateurs 64 bits, créez une sous\-clé sous la clé HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework dans la base de registres.  Utilisez le nom de clé LegacyMyComputerZone avec une valeur DWORD égale à 1.  Créez la même sous\-clé sous la clé HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework.  
  
## Voir aussi  
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)