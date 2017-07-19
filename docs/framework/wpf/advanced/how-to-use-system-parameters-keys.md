---
title: "Comment&#160;: utiliser les cl&#233;s des param&#232;tres syst&#232;me | Microsoft Docs"
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
  - "classes, SystemParameters"
  - "clés de ressource, SystemParameters (classe)"
  - "SystemParameters (classe)"
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: utiliser les cl&#233;s des param&#232;tres syst&#232;me
Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels conformes aux paramètres système.  <xref:System.Windows.SystemParameters> est une classe qui contient à la fois des valeurs de paramètre système et des clés de ressource qui créent des liaisons avec les valeurs, par exemple, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> et <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.  Les mesures de paramètres système peuvent être utilisées comme ressources statiques ou dynamiques.  Utilisez une ressource dynamique si vous souhaitez que la mesure de paramètre soit automatiquement mise à jour pendant l'exécution de l'application ; sinon, utilisez une ressource statique.  
  
> [!NOTE]
>  Pour les ressources dynamiques, le mot clé *Key* est ajouté au nom de propriété.  
  
 L'exemple suivant montre comment accéder aux ressources dynamiques de paramètre système et les utiliser pour appliquer un style ou personnaliser un bouton.  Cet exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dimensionne un bouton en attribuant des valeurs <xref:System.Windows.SystemParameters> à la largeur et à la hauteur d'un bouton.  
  
## Exemple  
 [!code-xml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## Voir aussi  
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [Utiliser des SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)   
 [Utiliser SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)