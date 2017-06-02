---
title: "Comment&#160;: d&#233;terminer si un Freezable est gel&#233; | Microsoft Docs"
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
  - "objets Freezable, déterminer s'ils sont figés"
  - "IsFrozen (propriété)"
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: d&#233;terminer si un Freezable est gel&#233;
Cet exemple indique comment déterminer si un objet <xref:System.Windows.Freezable> est gelé.  Si vous essayez de modifier un objet <xref:System.Windows.Freezable> gelé, il lève une <xref:System.InvalidOperationException>.  Pour éviter de lever cette exception, utilisez la propriété <xref:System.Windows.Freezable.IsFrozen%2A> de l'objet <xref:System.Windows.Freezable> pour déterminer s'il est gelé.  
  
## Exemple  
 L'exemple suivant gèle un <xref:System.Windows.Media.SolidColorBrush>, puis le teste à l'aide de la propriété <xref:System.Windows.Freezable.IsFrozen%2A> pour déterminer s'il est bien gelé.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Pour plus d'informations sur les objets <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.IsFrozen%2A>   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)