---
title: "Comment&#160;: positionner un menu contextuel personnalis&#233; dans un RichTextBox | Microsoft Docs"
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
  - "positionner des menus contextuels personnalisés"
  - "positionner des menus contextuels personnalisés"
  - "Contrôle RichTextBox, positionner des menus contextuels personnalisés"
  - "menus contextuels, de positionnement"
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: positionner un menu contextuel personnalis&#233; dans un RichTextBox
Cet exemple montre comment positionner un menu contextuel personnalisé pour un <xref:System.Windows.Controls.RichTextBox>.  
  
 Lorsque vous implémentez un menu contextuel personnalisé pour un **RichTextBox**, vous êtes chargé de gérer le positionnement du menu contextuel.  Par défaut, un menu contextuel personnalisé s’ouvre au centre de la **RichTextBox**.  
  
## <a name="example"></a>Exemple  
 Pour substituer le comportement de positionnement par défaut, ajoutez un écouteur pour le <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> événement.  L’exemple suivant montre comment effectuer cette opération par programme.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une implémentation correspondants <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> écouteur d’événements.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [Vue d’ensemble de la zone de texte](../../../../docs/framework/wpf/controls/textbox-overview.md)