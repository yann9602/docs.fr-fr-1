---
title: "Comment&#160;: utiliser SystemParameters | Microsoft Docs"
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
  - "SystemParameters (classe)"
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: utiliser SystemParameters
Cet exemple montre comment accéder aux propriétés de <xref:System.Windows.SystemParameters> et les utiliser pour appliquer un style ou personnaliser un bouton.  
  
## Exemple  
 Les ressources système exposent plusieurs paramètres système en tant que ressources pour vous aider à créer des visuels conformes aux paramètres système.  <xref:System.Windows.SystemParameters> est une classe qui contient à la fois des propriétés de valeur de paramètre système et des clés de ressource qui créent des liaisons avec les valeurs.  Par exemple, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> est une valeur de propriété <xref:System.Windows.SystemParameters> et <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> est la clé de ressource correspondante.  
  
 En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemParameters> comme utilisation de propriété statique ou comme références d'une ressource dynamique \(la valeur de la propriété statique étant la clé\).  Utilisez une référence de ressource dynamique si vous souhaitez que la valeur basée sur le système soit automatiquement mise à jour pendant l'exécution de l'application ; sinon, utilisez une référence statique.  Pour les clés de ressources, le suffixe `Key` est ajouté au nom de propriété.  
  
 L'exemple suivant montre comment accéder aux valeurs statiques de <xref:System.Windows.SystemParameters> et les utiliser pour appliquer un style ou personnaliser un bouton.  Cet exemple de balisage dimensionne un bouton en appliquant des valeurs <xref:System.Windows.SystemParameters> à un bouton.  
  
 [!code-xml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Pour utiliser les valeurs de <xref:System.Windows.SystemParameters> dans le code, vous ne devez pas utiliser de références statiques ou de références de ressource dynamique.  À la place, utilisez les valeurs de la classe <xref:System.Windows.SystemParameters>.  Bien que les propriétés ne correspondant pas à une clé soient apparemment définies en tant que propriétés statiques, le comportement au moment de l'exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tel qu'il est hébergé par le système réévalue les propriétés en temps réel et tient compte des modifications utilisateur apportées aux valeurs système. L'exemple suivant montre comment définir la largeur et la hauteur d'un bouton à l'aide de valeurs <xref:System.Windows.SystemParameters>.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## Voir aussi  
 <xref:System.Windows.SystemParameters>   
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)   
 [Utiliser des SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)   
 [Utiliser les clés des paramètres système](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)