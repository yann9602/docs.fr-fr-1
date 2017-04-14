---
title: "Comment&#160;: mettre un Freezable en lecture seule | Microsoft Docs"
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
  - "objets Freezable, rendre en lecture seule"
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: mettre un Freezable en lecture seule
Cet exemple indique comment mettre un <xref:System.Windows.Freezable> en lecture seule en appelant sa méthode <xref:System.Windows.Freezable.Freeze%2A>.  
  
 Vous ne pouvez pas geler un objet <xref:System.Windows.Freezable> si l'une des conditions suivantes est `true` à propos de l'objet :  
  
-   Il dispose de propriétés animées ou liées aux données.  
  
-   Il dispose de propriétés définies par une ressource dynamique.  Pour plus d'informations sur les ressources dynamiques, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Il contient des sous\-objets <xref:System.Windows.Freezable> qui ne peuvent pas être gelés.  
  
 Si ces conditions sont `false` pour votre objet <xref:System.Windows.Freezable> et que vous ne projetez pas de le modifier, envisagez de le geler pour gagner des avantages de performance.  
  
## Exemple  
 L'exemple suivant gèle un <xref:System.Windows.Media.SolidColorBrush>, c'est\-à\-dire un type d'objet <xref:System.Windows.Freezable>.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.CanFreeze%2A>   
 <xref:System.Windows.Freezable.Freeze%2A>   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)