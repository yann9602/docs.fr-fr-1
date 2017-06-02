---
title: "Comment&#160;: utiliser un menu contextuel personnalis&#233; avec un TextBox | Microsoft Docs"
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
  - "menus contextuels, personnalisé"
  - "menus contextuels personnalisés"
  - "menus, personnalisé"
  - "TextBox (contrôle), menus contextuels personnalisés"
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: utiliser un menu contextuel personnalis&#233; avec un TextBox
Cet exemple montre comment définir et implémenter un menu contextuel personnalisé simple pour un contrôle <xref:System.Windows.Controls.TextBox>.  
  
## Exemple  
 L'exemple [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant définit un contrôle <xref:System.Windows.Controls.TextBox> qui inclut un menu contextuel personnalisé.  
  
 Le menu contextuel est défini à l'aide d'un élément <xref:System.Windows.Controls.ContextMenu>.  Le menu contextuel lui\-même est constitué d'une série d'éléments <xref:System.Windows.Controls.MenuItem> et <xref:System.Windows.Controls.Separator>.  Chaque élément <xref:System.Windows.Controls.MenuItem> définit une commande du menu contextuel ; l'attribut <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> définit le texte affiché pour la commande de menu, tandis que l'attribut <xref:System.Windows.Controls.MenuItem.Click> spécifie une méthode de gestionnaire pour chaque élément de menu.  L'élément <xref:System.Windows.Controls.Separator> provoque simplement le rendu d'une ligne de séparation entre les éléments de menu précédents et suivants.  
  
 [!code-xml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## Exemple  
 L'exemple suivant montre le code d'implémentation pour la définition de menu contextuel précédente, de même que le code qui active et désactive le menu contextuel.  L'événement <xref:System.Windows.Controls.ContextMenu.Opened> est utilisé pour activer ou désactiver certaines commandes de manière dynamique selon l'état actuel de <xref:System.Windows.Controls.TextBox>.  
  
 Pour restaurer le menu contextuel par défaut, utilisez la méthode <xref:System.Windows.DependencyObject.ClearValue%2A> pour effacer la valeur de la propriété <xref:System.Windows.FrameworkElement.ContextMenu%2A>.  Pour désactiver complètement le menu contextuel, affectez une référence nulle \(`Nothing` dans Visual Basic\) à la propriété <xref:System.Windows.FrameworkElement.ContextMenu%2A>.  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## Voir aussi  
 [Utiliser la vérification de l'orthographe avec un menu contextuel](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)   
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)