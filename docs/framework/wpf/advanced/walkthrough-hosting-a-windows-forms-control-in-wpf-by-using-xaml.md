---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le Windows Forms dans WPF avec XAML | Microsoft Docs"
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
  - "héberger un contrôle Windows Forms dans WPF"
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le Windows Forms dans WPF avec XAML
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit de nombreux contrôles dotés d'un ensemble de fonctionnalités riche.  Toutefois, vous pouvez parfois souhaiter utiliser des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sur vos pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Par exemple, vous pouvez avoir un investissement substantiel dans les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] existants, ou vous pouvez avoir un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui fournit des fonctionnalités uniques.  
  
 Cette procédure pas à pas vous indique comment héberger un contrôle de Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=fullName> sur une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Pour obtenir l'intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [Hébergement d'un contrôle Windows Forms dans Windows Presentation Foundation avec XAML, exemple](http://go.microsoft.com/fwlink/?LinkID=160000).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## Hébergement du contrôle Windows Forms  
  
#### Pour héberger le contrôle MaskedTextBox  
  
1.  Créez un projet d'application WPF nommé `HostingWfInWpfWithXaml`.  
  
2.  Ajoutez des références aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Ouvrez MainWindow.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  Dans l'élément <xref:System.Windows.Window>, ajoutez le mappage d'espaces de noms suivant.  Le mappage de l'espace de noms `wf` établit une référence à l'assembly qui contient le contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Dans l'élément <xref:System.Windows.Controls.Grid>, ajoutez le code XAML suivant.  
  
     Le contrôle <xref:System.Windows.Forms.MaskedTextBox> est créé comme enfant du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
     [!code-xml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  Appuyez sur F5 pour générer et exécuter l'application.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Contrôles Windows Forms et contrôles WPF équivalents](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)   
 [Hébergement d'un contrôle Windows Forms dans Windows Presentation Foundation avec XAML, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160000)