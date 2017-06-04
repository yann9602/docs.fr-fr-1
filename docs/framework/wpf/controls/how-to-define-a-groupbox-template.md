---
title: "Comment&#160;: d&#233;finir un mod&#232;le GroupBox | Microsoft Docs"
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
  - "contrôles, GroupBox"
  - "GroupBox (contrôle), créer des modèles"
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;finir un mod&#232;le GroupBox
Cet exemple montre comment créer un modèle pour un contrôle <xref:System.Windows.Controls.GroupBox>.  
  
## Exemple  
 L'exemple suivant définit un modèle de contrôle <xref:System.Windows.Controls.GroupBox> à l'aide d'un contrôle <xref:System.Windows.Controls.Grid> pour la disposition.  Le modèle utilise un <xref:System.Windows.Controls.BorderGapMaskConverter> pour définir la bordure du <xref:System.Windows.Controls.GroupBox> afin que la bordure ne masque pas le contenu <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.  
  
 [!code-xml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.GroupBox>   
 [GroupBox How\-to Topics](http://msdn.microsoft.com/fr-fr/7692e155-a4c6-428c-b7e0-64b3740daca7)