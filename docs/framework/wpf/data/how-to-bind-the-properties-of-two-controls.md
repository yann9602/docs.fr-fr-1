---
title: "Comment&#160;: lier les propri&#233;t&#233;s de deux contr&#244;les | Microsoft Docs"
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
  - "lier les propriétés de deux contrôles"
  - "contrôles, lier les propriétés de"
  - "liaison de données, lier les propriétés de deux contrôles"
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: lier les propri&#233;t&#233;s de deux contr&#244;les
Cet exemple indique comment lier la propriété d'un contrôle instancié à celle d'un autre à l'aide de la propriété <xref:System.Windows.Data.Binding.ElementName%2A>.  
  
## Exemple  
 L'exemple suivant montre comment lier la propriété <xref:System.Windows.Controls.Panel.Background%2A> d'un <xref:System.Windows.Controls.Canvas> à la propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> d'un <xref:System.Windows.Controls.ComboBox> :  
  
 [!code-xml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Lorsque cet exemple est restitué il se présente de la manière suivante :  
  
 ![Canevas avec arrière&#45;plan vert](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.png "DataBindingBindingDPsSample")  
  
 **Remarque** La propriété [de cible de la liaison](GTMT) \(dans cet exemple, la propriété <xref:System.Windows.Controls.Panel.Background%2A>\) doit être une [propriété de dépendance](GTMT).  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## Voir aussi  
 [Spécifier la source de liaison](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)