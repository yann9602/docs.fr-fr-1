---
title: "Comment&#160;: cr&#233;er un contr&#244;le avec touche d&#39;acc&#232;s rapide et habillage du texte | Microsoft Docs"
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
  - "touches d'accès rapide, contrôle pour"
  - "contrôles, touches d'accès rapide"
  - "contrôles, habillage du texte"
  - "clés, contrôle pour"
  - "habillage du texte"
  - "renvoyer automatiquement du texte à la ligne"
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: cr&#233;er un contr&#244;le avec touche d&#39;acc&#232;s rapide et habillage du texte
Cet exemple montre comment créer un contrôle pourvu d'une [touche d'accès rapide](GTMT) et prenant en charge l'habillage du texte.  L'exemple utilise un contrôle <xref:System.Windows.Controls.Label> pour illustrer ces concepts.  
  
## Exemple  
 **Ajouter de l'habillage du texte à votre étiquette**  
  
 Le contrôle <xref:System.Windows.Controls.Label> ne prend pas en charge l'habillage du texte.  Si vous avez besoin d'une étiquette couvrant plusieurs lignes, vous pouvez imbriquer un autre élément qui prend en charge l'habillage du texte et le placer à l'intérieur de l'étiquette.  L'exemple suivant montre comment utiliser un <xref:System.Windows.Controls.TextBlock> pour faire une étiquette couvrant plusieurs lignes de texte.  
  
 [!code-xml[Label#5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Label/XAML/Pane1.xaml#5)]
 [!code-xml[Label#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Label/CS/Pane1.xaml#5)]  
  
 **Ajouter une touche d'accès rapide et de l'habillage du texte à votre étiquette**  
  
 Si vous avez besoin d'un <xref:System.Windows.Controls.Label> possédant une touche d'accès rapide \(mnémonique\), utilisez l'élément <xref:System.Windows.Controls.AccessText> situé à l'intérieur du <xref:System.Windows.Controls.Label>.  
  
 Des contrôles tels que <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander> et <xref:System.Windows.Controls.GroupBox> possèdent des modèles de contrôle par défaut.  Ces modèles contiennent un <xref:System.Windows.Controls.ContentPresenter>.  L'une des propriétés que vous pouvez définir sur le <xref:System.Windows.Controls.ContentPresenter> est <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>\= "vrai", que vous pouvez utiliser pour spécifier une touche d'accès rapide pour le contrôle.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Controls.Label> pourvu d'une touche d'accès rapide et prenant en charge l'habillage du texte.  Pour activer l'habillage du texte, l'exemple définit la propriété <xref:System.Windows.Controls.AccessText.TextWrapping%2A> et utilise un caractère de soulignement pour spécifier la touche d'accès rapide.  \(Le caractère qui suit immédiatement le caractère de soulignement est la touche d'accès rapide.\)  
  
 [!code-xml[Label#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Label/XAML/Pane1.xaml#4)]
 [!code-xml[Label#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Label/CS/Pane1.xaml#4)]  
  
## Voir aussi  
 [How to: Set the Target Property of a Label](http://msdn.microsoft.com/fr-fr/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)