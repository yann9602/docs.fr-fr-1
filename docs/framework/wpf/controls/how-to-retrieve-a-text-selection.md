---
title: "Comment&#160;: r&#233;cup&#233;rer une s&#233;lection de texte | Microsoft Docs"
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
  - "récupérer du texte"
  - "texte, récupérer"
  - "TextBox (contrôle), récupérer du texte"
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: r&#233;cup&#233;rer une s&#233;lection de texte
Cet exemple montre une méthode pour utiliser la propriété <xref:System.Windows.Controls.TextBox.SelectedText%2A> pour récupérer du texte sélectionné par l'utilisateur dans un contrôle <xref:System.Windows.Controls.TextBox>.  
  
## Exemple  
 L'exemple [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant montre la définition d'un contrôle <xref:System.Windows.Controls.TextBox> qui contient du texte à sélectionner, et un contrôle <xref:System.Windows.Controls.Button> associé à une méthode <xref:System.Windows.Controls.Button.OnClick%2A> spécifiée.  
  
 Dans cet exemple, un bouton avec un gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> associé est utilisé pour récupérer la sélection de texte.  Lorsque l'utilisateur clique sur le bouton, la méthode <xref:System.Windows.Controls.Button.OnClick%2A> copie le texte sélectionné de la zone de texte dans une chaîne.  Les cas particuliers dans lesquels la sélection de texte est récupérée \(en cliquant sur un bouton\), ainsi que l'action effectuée avec cette sélection \(copie de la sélection de texte dans une chaîne\), peuvent être facilement modifiés pour s'adapter à une grande variété de scénarios.  
  
 [!code-xml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## Exemple  
 L'exemple [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] suivant montre un gestionnaire d'événements <xref:System.Windows.Controls.Button.OnClick%2A> pour le bouton défini en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour cet exemple.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## Voir aussi  
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)