---
title: "Comment&#160;: effectuer une liaison &#224; une &#233;num&#233;ration | Microsoft Docs"
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
  - "lier des données, énumération"
  - "liaison de données, énumération"
  - "énumération"
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: effectuer une liaison &#224; une &#233;num&#233;ration
Cet exemple montre comment effectuer une liaison à une énumération en utilisant la méthode GetValues de l'énumération.  
  
## Exemple  
 Dans l'exemple suivant, <xref:System.Windows.Controls.ListBox> affiche la liste des valeurs de l'énumération <xref:System.Windows.HorizontalAlignment> obtenues via la liaison de données.  Les contrôles <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.Button> sont liés de telle sorte que vous pouvez modifier la valeur de la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> de <xref:System.Windows.Controls.Button> en sélectionnant une valeur dans <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## Voir aussi  
 [Effectuer une liaison à une méthode](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)