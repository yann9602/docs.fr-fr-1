---
title: "Comment&#160;: appeler une bo&#238;te de dialogue Imprimer | Microsoft Docs"
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
  - "appeler des boîtes de dialogue d'impression"
  - "boîtes de dialogue d'impression, appeler"
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: appeler une bo&#238;te de dialogue Imprimer
Pour vous permettre d'imprimer depuis votre application, vous pouvez simplement créer et ouvrir un objet <xref:System.Windows.Controls.PrintDialog>.  
  
## Exemple  
 Le contrôle <xref:System.Windows.Controls.PrintDialog> fournit un point d'entrée unique pour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], la configuration, et la soumission de travaux [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)].  Le contrôle est simple d'utilisation et peut être instancié à l'aide du code ou du balisage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  L'exemple suivant montre comment instancier et ouvrir le contrôle dans le code et comment imprimer à partir de lui.  Il indique également comment garantir que la boîte de dialogue fournira à l'utilisateur l'option de définir une plage de pages spécifique.  Cet exemple de code suppose qu'il existe un fichier FixedDocumentSequence.xps dans la racine du lecteur C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Une fois que la boîte de dialogue est ouverte, les utilisateurs pourront sélectionner l'une des imprimantes installées sur leur ordinateur.  Ils pourront également sélectionner [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) pour créer un fichier [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] au lieu d'imprimer.  
  
> [!NOTE]
>  Le contrôle <xref:System.Windows.Controls.PrintDialog?displayProperty=fullName> de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], qui est abordé dans cette rubrique, ne doit pas être confondu avec le composant <xref:System.Windows.Forms.PrintDialog?displayProperty=fullName> de [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  
  
 En principe, vous pouvez utiliser la méthode <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> sans jamais ouvrir la boîte de dialogue.  Dans ce sens, le contrôle est utilisé comme un composant d'impression inaperçu.  Toutefois, pour des raisons de performances, il est préférable d'utiliser la méthode <xref:System.Printing.PrintQueue.AddJob%2A> ou l'une des nombreuses méthodes<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> du <xref:System.Windows.Xps.XpsDocumentWriter>.  Pour plus d'informations à ce sujet, consultez [Imprimer des fichiers XPS par programmation](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md).  
  
## Voir aussi  
 <xref:System.Windows.Controls.PrintDialog>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Microsoft XPS Document Writer \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=147319)