---
title: "Comment : activer des styles visuels dans une application hybride"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e628835f0e5fb315f15b9e9946c48f7017092bae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Comment : activer des styles visuels dans une application hybride
Cette rubrique montre comment activer [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] styles visuels sur un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle hébergé dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.  
  
 Si votre application appelle la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> (méthode), la plupart de vos [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles utiliseront automatiquement les styles visuels, lorsque votre application est exécutée sur [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Pour plus d’informations, consultez [de rendu des contrôles avec les Styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Pour l’intégralité du code des tâches illustrées dans cette rubrique, consultez [l’activation des Styles visuels dans une Application hybride, exemple](http://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Activation de styles visuels Windows Forms  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Pour activer les styles visuels Windows Forms  
  
1.  Créer un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projet d’Application nommé `HostingWfWithVisualStyles`.  
  
2.  Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Dans la boîte à outils, double-cliquez sur le <xref:System.Windows.Controls.Grid> icône pour placer un <xref:System.Windows.Controls.Grid> élément sur l’aire de conception.  
  
4.  Dans la fenêtre Propriétés, définissez les valeurs de la <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> propriétés **automatique**.  
  
5.  En mode Création ou la vue XAML, sélectionnez le <xref:System.Windows.Window>.  
  
6.  Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.  
  
7.  Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.
  
8.  Dans MainWindow.xaml.vb ou MainWindow.xaml.cs, insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Appuyez sur F5 pour générer et exécuter l'application.  
  
     Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est peint avec des styles visuels.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Désactivation de styles visuels Windows Forms  
 Pour désactiver des styles visuels, supprimez simplement l’appel à la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> (méthode).  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Pour désactiver les styles visuels Windows Forms  
  
1.  Ouvrez MainWindow.xaml.vb ou MainWindow.xaml.cs dans l’éditeur de code.  
  
2.  Commentez l’appel à la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> (méthode).  
  
3.  Appuyez sur F5 pour générer et exécuter l'application.  
  
     Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est peint avec le style du système par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
