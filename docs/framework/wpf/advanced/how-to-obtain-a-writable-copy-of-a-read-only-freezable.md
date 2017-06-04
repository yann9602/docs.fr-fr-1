---
title: "Comment&#160;: obtenir une copie en &#233;criture d&#39;un Freezable en lecture seule | Microsoft Docs"
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
  - "cloner des objets Freezable"
  - "objets Freezable, clones modifiables"
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: obtenir une copie en &#233;criture d&#39;un Freezable en lecture seule
Cet exemple montre comment utiliser la méthode <xref:System.Windows.Freezable.Clone%2A> pour créer une copie en écriture d'un <xref:System.Windows.Freezable> en lecture seule.  
  
 Une fois qu'un objet <xref:System.Windows.Freezable> est marqué en lecture seule \(« figé »\), vous ne pouvez pas le modifier.  Toutefois, vous pouvez utiliser la méthode <xref:System.Windows.Freezable.Clone%2A> pour créer un clone modifiable de l'objet figé.  
  
## Exemple  
 L'exemple suivant crée un clone modifiable d'un objet <xref:System.Windows.Media.SolidColorBrush> figé.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)