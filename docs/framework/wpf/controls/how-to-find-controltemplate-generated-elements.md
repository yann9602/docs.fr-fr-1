---
title: "Rechercher des &#233;l&#233;ments g&#233;n&#233;r&#233;s par ControlTemplate | Microsoft Docs"
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
  - "ControlTemplates (WPF), rechercher des éléments"
  - "rechercher des éléments ControlTemplate"
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Rechercher des &#233;l&#233;ments g&#233;n&#233;r&#233;s par ControlTemplate
Cet exemple montre comment rechercher des éléments qui sont générés par <xref:System.Windows.Controls.ControlTemplate>.  
  
## Exemple  
 L'exemple suivant montre un style qui crée un <xref:System.Windows.Controls.ControlTemplate> simple pour la classe <xref:System.Windows.Controls.Button> :  
  
 [!code-xml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Pour rechercher un élément dans le modèle une fois que celui\-ci a été appliqué, vous pouvez appeler la méthode <xref:System.Windows.FrameworkTemplate.FindName%2A> du <xref:System.Windows.Controls.Control.Template%2A>.  L'exemple suivant crée un message qui affiche la largeur réelle de la <xref:System.Windows.Controls.Grid> dans le modèle de contrôle :  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## Voir aussi  
 [Rechercher des éléments générés par DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Portées de nom XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)   
 [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)