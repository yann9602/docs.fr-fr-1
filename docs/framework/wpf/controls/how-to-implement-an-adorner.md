---
title: "Comment&#160;: impl&#233;menter un ornement | Microsoft Docs"
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
  - "ornements, implémenter"
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: impl&#233;menter un ornement
Cet exemple montre une implémentation d'ornement minimale.  
  
## Remarques à l'intention des implémenteurs  
 Il est important de noter que les ornements n'incluent aucun comportement de rendu inhérent ; garantissant que le rendu d'un ornement est la responsabilité de l'implémenteur d'ornement.  Un moyen courant d'implémentation du comportement de rendu est de remplacer la méthode <xref:System.Windows.UIElement.OnRender%2A> et d'utiliser un ou plusieurs objets <xref:System.Windows.Media.DrawingContext> pour restituer les visuels de l'ornement en fonction des besoins \(comme illustré cet exemple\).  
  
## Exemple  
  
### Description  
 Un ornement personnalisé est créé en implémentant une classe qui hérite de la classe abstraite <xref:System.Windows.Documents.Adorner>.  L'ornement d'exemple orne simplement les angles d'un <xref:System.Windows.UIElement> avec des cercles en substituant la méthode <xref:System.Windows.UIElement.OnRender%2A>.  
  
### Code  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## Voir aussi  
 [Vue d'ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md)