---
title: "Comment&#160;: ajouter un filigrane &#224; un TextBox | Microsoft Docs"
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
  - "faciliter l'utilisation d'un TextBox à l'aide d'une image d'arrière-plan (WPF)"
  - "afficher une image d'arrière-plan dans une zone de texte pour faciliter l'entrée d'utilisateur (WPF)"
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: ajouter un filigrane &#224; un TextBox
L'exemple suivant indique comment faciliter l'utilisation d'un <xref:System.Windows.Controls.TextBox> en affichant une image d'arrière\-plan explicative dans le <xref:System.Windows.Controls.TextBox> jusqu'à ce que l'utilisateur entre du texte, après quoi l'image est supprimée.  De plus, l'image d'arrière\-plan est restaurée si l'utilisateur supprime son entrée.  Voyez l'illustration ci\-dessous.  
  
 ![TextBox avec image d'arrière&#45;plan](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing\_TextBox\_using\_background\_image")  
  
> [!NOTE]
>  Cet exemple utilise une image d'arrière\-plan au lieu de simplement manipuler la propriété <xref:System.Windows.Controls.TextBox.Text%2A> du <xref:System.Windows.Controls.TextBox>, parce qu'une image d'arrière\-plan n'interfère pas avec la liaison de données.  
  
## Exemple  
 [!code-xml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## Voir aussi  
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)