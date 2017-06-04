---
title: "H&#244;te WPF (PresentationHost.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PresentationHost.exe"
  - "WPF (application hôte)"
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# H&#244;te WPF (PresentationHost.exe)
L'hôte [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] \(PresentationHost.exe\) est une application qui permet aux applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] d'être hébergées par des navigateurs compatibles \(y compris [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] et versions ultérieures\).  Par défaut, l'hôte [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] est enregistré comme l'interpréteur de commandes et gestionnaire [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] pour le contenu hébergé par navigateur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ce qui inclut :  
  
-   Fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libres \(.xaml\) \(non compilés\).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] \(.xbap\).  
  
 Pour les fichiers de ces types, l'hôte [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] :  
  
-   Lance le gestionnaire [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] enregistré pour héberger le contenu [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
-   Charge les bonnes versions des [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] requis et des assemblys [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
-   Garantit que les niveaux d'autorisation appropriés pour la zone de déploiement sont en place.  
  
 Cette rubrique décrit les paramètres de ligne de commande qui peuvent être utilisés avec PresentationHost.exe.  
  
## Utilisation  
 `PresentationHost.exe [parameters] uri|filename`  
  
## Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|filename|Chemin d'accès du fichier à activer.  Il peut également s'agir d'un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|\-debug|Lors de l'activation d'une application, ne la valide pas à ou l'exécute à partir du magasin.  Cela fonctionne seulement lorsqu'un fichier local est activé.|  
|\-debugSecurityZoneURL \<url\>|Utilisé avec une valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour indiquer à PresentationHost.exe qu'une application doit être déboguée comme si elle était déployée à partir de l'[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]spécifiée.  Cela détermine à la fois la zone de déploiement et le site d'origine.|  
|\-embedding|Requis par OLE.  Si le paramètre `-event` ou `-debug` est spécifié, il n'est pas nécessaire de spécifier le paramètre `-embedding`, puisque ce paramètre est défini en interne.|  
|\-event \<eventname\>|Ouvrez l'événement avec ce nom et signalez\-le lorsque PresentationHost.exe est initialisé et prêt à héberger le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  PresentationHost.exe se terminera si une erreur s'est produite lors de l'ouverture de l'événement, comme s'il n'avait pas encore été créé.|  
|\-launchApplication \<url\>|Lance une application [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] autonome depuis l'URL spécifiée.  Les stratégies de sécurité [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] et WinINet concernant les applications .NET sont appliquées.|  
  
## Scénarios  
  
### Gestionnaire de l'interpréteur de commandes  
 `PresentationHost.exe example.xbap`  
  
### Gestionnaire MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### Débogage Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### Zone d'entrée de débogage Visual Studio  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## Voir aussi  
 [Sécurité](../../../../docs/framework/wpf/security-wpf.md)