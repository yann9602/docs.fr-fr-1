---
title: "Comment&#160;: lier un ListBox &#224; des donn&#233;es | Microsoft Docs"
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
  - "lier des données, à un contrôle ListBox"
  - "liaison de données, ListBox (contrôle)"
  - "contrôles ListBox, lier des données à"
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: lier un ListBox &#224; des donn&#233;es
Un développeur d'applications peut créer des contrôles <xref:System.Windows.Controls.ListBoxItem> sans spécifier le contenu de chaque <xref:System.Windows.Controls.ListBox> séparément.  Vous pouvez utiliser la liaison de données pour lier des données aux éléments individuels.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Controls.ListBox> qui remplit les éléments <xref:System.Windows.Controls.ListBoxItem> à l'aide d'une liaison de données à une source de données appelée *Couleurs*.  Dans ce cas, il n'est pas nécessaire d'utiliser de balises <xref:System.Windows.Controls.ListBoxItem>pour spécifier le contenu de chaque élément.  
  
## Exemple  
 [!code-xml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.Controls.ListBoxItem>   
 [Contrôles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)