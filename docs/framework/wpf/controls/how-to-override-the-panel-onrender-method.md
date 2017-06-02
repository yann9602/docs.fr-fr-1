---
title: "Comment&#160;: substituer la m&#233;thode OnRender de Panel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "overriding OnRender method"
  - "Panel control, overriding OnRender method"
  - "OnRender method"
  - "controls, Panel, overriding OnRender method"
helpviewer_keywords: 
  - "OnRender (méthode), substituer"
  - "substituer la méthode OnRender du contrôle Panel"
  - "Panel (contrôle), substituer la méthode OnRender"
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: substituer la m&#233;thode OnRender de Panel
Cet exemple montre comment substituer la méthode <xref:System.Windows.Controls.Panel.OnRender%2A> de <xref:System.Windows.Controls.Panel> pour ajouter des effets graphiques personnalisés à un élément de disposition.  
  
## Exemple  
 Utilisez la méthode <xref:System.Windows.Controls.Panel.OnRender%2A> pour ajouter des effets graphiques à un élément de panneau rendu.  Par exemple, vous pouvez utiliser cette méthode pour ajouter une bordure personnalisée ou des effets d'arrière\-plan.  Un objet <xref:System.Windows.Media.DrawingContext> est passé comme un argument qui fournit des méthodes pour dessiner des formes, du texte, des images ou des vidéos.  Par conséquent, cette méthode est utile pour la personnalisation d'un objet de panneau.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Panel>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Panneau radial personnalisé, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159982)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)