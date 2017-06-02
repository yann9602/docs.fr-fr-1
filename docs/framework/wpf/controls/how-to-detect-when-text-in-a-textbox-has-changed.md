---
title: "Comment&#160;: d&#233;tecter la modification du texte figurant dans un TextBox | Microsoft Docs"
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
  - "détecter une modification du texte"
  - "modification du texte, détecter"
  - "TextBox (contrôle), détecter une modification du texte"
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;tecter la modification du texte figurant dans un TextBox
Cet exemple illustre une façon d'utiliser l'événement <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> pour exécuter une méthode lorsque le texte d'un contrôle <xref:System.Windows.Controls.TextBox> change.  
  
 Dans la classe code\-behind du langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le contrôle <xref:System.Windows.Controls.TextBox> dont vous souhaitez suivre les modifications, insérez une méthode à appeler à chaque fois que l'événement <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se déclenche.  Cette méthode doit comporter une signature correspondant à celle attendue par le délégué <xref:System.Windows.Controls.TextChangedEventHandler>.  
  
 Le gestionnaire d'événements est appelé lorsque le contenu du contrôle <xref:System.Windows.Controls.TextBox> est modifié \(par un utilisateur ou par programme\).  
  
 **Remarque :** cet événement se déclenche lorsque le contrôle <xref:System.Windows.Controls.TextBox> est créé et rempli initialement de texte.  
  
## Exemple  
 Dans le langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui définit votre contrôle <xref:System.Windows.Controls.TextBox>, spécifiez l'attribut <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> avec une valeur qui correspond au nom de la méthode du gestionnaire d'événements.  
  
 [!code-xml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## Exemple  
 Dans la classe code\-behind du langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui contient le contrôle <xref:System.Windows.Controls.TextBox> dont vous souhaitez suivre les modifications, insérez une méthode à appeler à chaque fois que l'événement <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> se déclenche.  Cette méthode doit comporter une signature correspondant à celle attendue par le délégué <xref:System.Windows.Controls.TextChangedEventHandler>.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Le gestionnaire d'événements est appelé lorsque le contenu du contrôle <xref:System.Windows.Controls.TextBox> est modifié \(par un utilisateur ou par programme\).  
  
 **Remarque :** cet événement se déclenche lorsque le contrôle <xref:System.Windows.Controls.TextBox> est créé et rempli initialement de texte.  
  
 Commentaires  
  
## Voir aussi  
 <xref:System.Windows.Controls.TextChangedEventArgs>   
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)