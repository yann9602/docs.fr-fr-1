---
title: "Comment&#160;: cr&#233;er un bouton comportant une image | Microsoft Docs"
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
  - "contrôles bouton (WPF), créer"
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er un bouton comportant une image
Cet exemple indique comment inclure une image sur un <xref:System.Windows.Controls.Button>.  
  
## Exemple  
 L'exemple suivant crée deux contrôles <xref:System.Windows.Controls.Button>.  L'un des <xref:System.Windows.Controls.Button>s contient du texte et l'autre une image.  L'image est dans un dossier appelé données, qui est un sous\-dossier du dossier de projet de l'exemple.  Lorsqu'un utilisateur clique sur le <xref:System.Windows.Controls.Button> avec l'image, l'arrière\-plan et le texte de l'autre <xref:System.Windows.Controls.Button> changent.  
  
 Cet exemple crée des contrôles <xref:System.Windows.Controls.Button> à l'aide du balisage, mais il utilise du code pour écrire les gestionnaires d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
 [!code-xml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## Voir aussi  
 [Contrôles](../../../../docs/framework/wpf/controls/index.md)   
 [Bibliothèque de contrôles](../../../../docs/framework/wpf/controls/control-library.md)