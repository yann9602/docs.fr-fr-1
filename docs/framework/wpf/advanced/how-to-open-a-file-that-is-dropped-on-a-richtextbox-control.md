---
title: "Comment&#160;: ouvrir un fichier qui est d&#233;plac&#233; dans un contr&#244;le RichTextBox | Microsoft Docs"
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
  - "glisser-déplacer (WPF), ouvrir un fichier déplacé"
  - "glisser-déplacer (WPF), RichTextBox"
  - "RichTextBox (WPF), glisser et déposer"
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: ouvrir un fichier qui est d&#233;plac&#233; dans un contr&#244;le RichTextBox
Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les contrôles <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Documents.FlowDocument> possèdent tous la fonctionnalité glisser\-déplacer intégrée.  La fonctionnalité intégrée active le glisser\-déplacer de texte à l'intérieur et entre les contrôles.  Toutefois, elle n'active pas l'ouverture d'un fichier en déplaçant le fichier sur le contrôle.  Ces contrôles marquent également les événements de glisser\-déplacer comme exécutés.  En conséquence, vous ne pouvez pas ajouter par défaut vos propres gestionnaires d'événements pour fournir des fonctionnalités d'ouverture des fichiers déplacés.  
  
 Pour ajouter une gestion supplémentaire des événements glisser\-déplacer dans ces contrôles, utilisez la méthode <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> pour ajouter vos gestionnaires d'événements pour les événements glisser\-déplacer.  Affectez la valeur `true` au paramètre `handledEventsToo` pour que le gestionnaire spécifié soit appelé pour un événement routé déjà marqué comme géré par un autre élément sur l'itinéraire d'événement.  
  
> [!TIP]
>  Vous pouvez remplacer la fonctionnalité de glisser\-déplacer intégrée de <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Documents.FlowDocument> en gérant les versions d'aperçu des événements glisser\-déplacer et en marquant les événements d'aperçu comme exécutés.  Toutefois, cela désactive la fonctionnalité de glisser\-déplacer intégrée, ce qui n'est pas recommandé.  
  
## Exemple  
 L'exemple suivant montre comment ajouter des gestionnaires pour les événements <xref:System.Windows.DragDrop.DragOver> et <xref:System.Windows.DragDrop.Drop> sur une <xref:System.Windows.Controls.RichTextBox>.  Cet exemple utilise la méthode <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> et affecte la valeur `true` au paramètre `handledEventsToo` de manière à ce que afin que les gestionnaires d'événements soient appelés même si la <xref:System.Windows.Controls.RichTextBox> marque ces événements comme exécutés.  Le code des gestionnaires d'événement ajoute une fonctionnalité d'ouverture d'un fichier qui est déplacé sur la <xref:System.Windows.Controls.RichTextBox>.  
  
 Pour tester cet exemple, faites glisser un fichier texte ou un fichier au format RTF \(Rich Text Format\) depuis l'Explorateur Windows vers la <xref:System.Windows.Controls.RichTextBox>.  Le fichier doit être ouvert dans la <xref:System.Windows.Controls.RichTextBox>.  Si vous appuyez sur la touche MAJ avant de déplacer le fichier, le fichier sera ouvert en texte brut.  
  
 [!code-xml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]