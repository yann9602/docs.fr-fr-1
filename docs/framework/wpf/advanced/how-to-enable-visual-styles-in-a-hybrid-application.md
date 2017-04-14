---
title: "Comment&#160;: activer des styles visuels dans une application hybride | Microsoft Docs"
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
  - "applications hybrides (interopérabilité WPF)"
  - "styles visuels (Windows Forms)"
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: activer des styles visuels dans une application hybride
Cette rubrique montre comment activer des styles visuels [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] sur un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Si votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, la plupart de vos contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] utiliseront automatiquement ces styles visuels lorsque votre application sera exécutée sur [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  Pour plus d'informations, consultez [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Pour obtenir l'intégralité du code des tâches illustrées dans cette rubrique, consultez [Activation des styles visuels dans une application hybride, exemple](http://go.microsoft.com/fwlink/?LinkID=159986).  
  
## Activation de styles visuels Windows Forms  
  
#### Pour activer les styles visuels Windows Forms  
  
1.  Créez un projet d'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nommé `HostingWfWithVisualStyles`.  
  
2.  Dans l'Explorateur de solutions, ajoutez une référence aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Dans la Boîte à outils, double\-cliquez sur l'icône <xref:System.Windows.Controls.Grid> pour placer un élément <xref:System.Windows.Controls.Grid> sur l'aire de conception.  
  
4.  Dans la fenêtre Propriétés, affectez la valeur **Auto** aux propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A>.  
  
5.  En mode Création ou vue XAML, sélectionnez <xref:System.Windows.Window>.  
  
6.  Dans la fenêtre Propriétés, cliquez sur l'onglet **Événements**.  
  
7.  Double\-cliquez sur l'événement <xref:System.Windows.FrameworkElement.Loaded>.  
  
8.  Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, insérez le code suivant pour gérer l'événement <xref:System.Windows.FrameworkElement.Loaded>.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Appuyez sur F5 pour générer et exécuter l'application.  
  
     Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est peint avec des styles visuels.  
  
## Désactivation de styles visuels Windows Forms  
 Pour désactiver des styles visuels, supprimez simplement l'appel de la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
#### Pour désactiver les styles visuels Windows Forms  
  
1.  Ouvrez MainWindow.xaml.vb ou MainWindow.xaml.cs dans l'Éditeur de code.  
  
2.  Commentez l'appel de la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
     Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est peint avec le style par défaut du système.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>   
 <xref:System.Windows.Forms.VisualStyles>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)   
 [Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)