---
title: "Comment&#160;: utiliser des SystemFonts | Microsoft Docs"
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
  - "polices, polices système"
  - "polices système"
  - "SystemFonts (classe)"
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Comment&#160;: utiliser des SystemFonts
Cet exemple montre comment utiliser les ressources statiques de la classe <xref:System.Windows.SystemFonts> pour appliquer un style ou personnaliser un bouton.  
  
## Exemple  
 Les ressources système exposent plusieurs valeurs déterminées par le système en tant que ressources et propriétés pour vous aider à créer des visuels conformes aux paramètres système.  <xref:System.Windows.SystemFonts> est une classe qui contient à la fois des valeurs de police système en tant que propriétés statiques et des propriétés qui référencent des clés de ressource pouvant être utilisées pour accéder dynamiquement à ces valeurs au moment de l'exécution.  Par exemple, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> est une valeur <xref:System.Windows.SystemFonts> et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> est une clé de ressource correspondante.  
  
 En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemFonts> comme propriétés statiques ou références de ressource dynamique \(la valeur de la propriété statique étant la clé\).  Utilisez une référence de ressource dynamique si vous souhaitez que la métrique de police soit automatiquement mise à jour pendant l'exécution de l'application ; sinon, utilisez une référence de valeur statique.  
  
> [!NOTE]
>  Pour les clés de ressources, le suffixe « Key » est ajouté au nom de propriété.  
  
 L'exemple suivant montre comment accéder aux propriétés de <xref:System.Windows.SystemFonts> et les utiliser comme valeurs statiques pour appliquer un style ou personnaliser un bouton.  Cet exemple de balisage assigne des valeurs <xref:System.Windows.SystemFonts> à un bouton.  
  
 [!code-xml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Pour utiliser les valeurs de <xref:System.Windows.SystemFonts> dans le code, vous ne devez pas utiliser de référence de ressource dynamique ou de valeur statique.  Utilisez plutôt les propriétés ne correspondant pas à une clé de la classe <xref:System.Windows.SystemFonts>.  Bien que les propriétés ne correspondant pas à une clé soient apparemment définies comme propriétés statiques, le comportement au moment de l'exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tel qu'il est hébergé par le système réévaluera les propriétés en temps réel et tiendra compte des modifications utilisateur apportées aux valeurs système.  L'exemple suivant montre comment spécifier les paramètres de police d'un bouton.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## Voir aussi  
 <xref:System.Windows.SystemFonts>   
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [Utiliser SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)   
 [Utiliser des clés de polices système](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)   
 [x:Static, extension de balisage](../../../../docs/framework/xaml-services/x-static-markup-extension.md)   
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)