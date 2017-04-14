---
title: "Comment&#160;: utiliser des cl&#233;s de polices syst&#232;me | Microsoft Docs"
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
  - "classes, SystemFonts"
  - "clés de ressource, SystemFonts (classe)"
  - "SystemFonts (classe)"
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: utiliser des cl&#233;s de polices syst&#232;me
Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels conformes aux paramètres système.  <xref:System.Windows.SystemFonts> est une classe qui contient à la fois des valeurs de police système et des ressources de police système liées aux valeurs, par exemple <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Les mesures de police système peuvent être utilisées comme ressources statiques ou dynamiques.  Utilisez une ressource dynamique si vous souhaitez que la mesure de police soit automatiquement mise à jour pendant l'exécution de l'application ; sinon, utilisez une ressource statique.  
  
> [!NOTE]
>  Pour les ressources dynamiques, le mot clé *Key* est ajouté au nom de propriété.  
  
 L'exemple suivant montre comment accéder aux ressources dynamiques de police système et les utiliser pour appliquer un style ou personnaliser un bouton.  Cet exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] crée un style de boutons qui assigne des valeurs <xref:System.Windows.SystemFonts> à un bouton.  
  
## Exemple  
 [!code-xml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## Voir aussi  
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [Utiliser SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)   
 [Utiliser des SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)