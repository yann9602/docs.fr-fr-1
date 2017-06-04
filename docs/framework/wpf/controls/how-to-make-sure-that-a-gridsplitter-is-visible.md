---
title: "Comment&#160;: v&#233;rifier qu&#39;un GridSplitter est visible | Microsoft Docs"
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
  - "GridSplitter (contrôle), garantir la visibilité de"
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: v&#233;rifier qu&#39;un GridSplitter est visible
Cet exemple montre comment vérifier qu'un contrôle <xref:System.Windows.Controls.GridSplitter> n'est pas masqué par les autres contrôles dans un <xref:System.Windows.Controls.Grid>.  
  
## Exemple  
 Les <xref:System.Windows.Controls.Panel.Children%2A> d'un contrôle <xref:System.Windows.Controls.Grid> sont restitués dans l'ordre dans lequel ils sont définis dans le balisage ou le code.  Les contrôles <xref:System.Windows.Controls.GridSplitter> peuvent être masqués par d'autres contrôles si vous ne les définissez pas en tant que derniers éléments dans la collection <xref:System.Windows.Controls.Panel.Children%2A> ou si vous donnez une <xref:System.Windows.Controls.Panel.ZIndexProperty> supérieure à d'autres contrôles.  
  
 Pour éviter que des contrôles <xref:System.Windows.Controls.GridSplitter> soient masqués, effectuez l'une des opérations suivantes.  
  
-   Vérifiez que les contrôles <xref:System.Windows.Controls.GridSplitter> sont les derniers <xref:System.Windows.Controls.Panel.Children%2A> ajoutés au <xref:System.Windows.Controls.Grid>.  L'exemple suivant présente le <xref:System.Windows.Controls.GridSplitter> comme le dernier élément de la collection <xref:System.Windows.Controls.Panel.Children%2A> du <xref:System.Windows.Controls.Grid>.  
  
 [!code-xml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   Définissez la <xref:System.Windows.Controls.Panel.ZIndexProperty> sur le <xref:System.Windows.Controls.GridSplitter> pour qu'elle soit plus élevée qu'un contrôle qui, sinon, la masquerait.  L'exemple suivant attribue au contrôle <xref:System.Windows.Controls.GridSplitter> une <xref:System.Windows.Controls.Panel.ZIndexProperty> plus élevée que le contrôle <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   Définissez des marges sur le contrôle qui, sinon, masquerait le <xref:System.Windows.Controls.GridSplitter> pour que le <xref:System.Windows.Controls.GridSplitter> soit exposé.  L'exemple suivant définit des marges sur un contrôle qui, sinon, chevaucherait et masquerait le <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.GridSplitter>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)