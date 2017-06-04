---
title: "Comment&#160;: obtenir une collection de lignes &#224; partir d&#39;un TextBox | Microsoft Docs"
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
  - "lignes, obtenir une collection de"
  - "TextBox (contrôle), obtenir une collection de lignes"
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: obtenir une collection de lignes &#224; partir d&#39;un TextBox
Cet exemple montre comment obtenir une collection de lignes de texte à partir d'une <xref:System.Windows.Controls.TextBox>.  
  
## Exemple  
 L'exemple suivant illustre une méthode simple qui utilise une <xref:System.Windows.Controls.TextBox> comme argument et retourne une <xref:System.Collections.Specialized.StringCollection> contenant les lignes de texte dans la **TextBox**.  La propriété <xref:System.Windows.Controls.TextBox.LineCount%2A> est utilisée pour déterminer le nombre actuel de lignes dans la **TextBox**. La méthode <xref:System.Windows.Controls.TextBox.GetLineText%2A> est ensuite utilisée pour extraire chaque ligne et l'ajouter à la collection de lignes.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## Voir aussi  
 [Vue d'ensemble de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)