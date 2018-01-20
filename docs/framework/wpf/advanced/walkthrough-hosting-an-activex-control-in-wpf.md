---
title: "Procédure pas à pas : hébergement d'un contrôle ActiveX dans WPF"
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
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0e85c715db30c6e577980376d25d56238e2835a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Procédure pas à pas : hébergement d'un contrôle ActiveX dans WPF
Pour permettre une interaction améliorée avec les navigateurs, vous pouvez utiliser [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] des contrôles dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur. Cette procédure pas à pas montre comment vous pouvez héberger le [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] comme un contrôle sur un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création du projet  
  
-   Création du contrôle ActiveX.  
  
-   Hébergement du contrôle ActiveX sur une Page WPF.  
  
 Lorsque vous avez terminé cette procédure pas à pas, vous saurez comment utiliser [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] des contrôles dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]installé sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet  
  
1.  Créez un projet d’Application WPF nommé `HostingAxInWpf`.  
  
2.  Ajouter un projet de bibliothèque de contrôles Windows Forms à la solution et nommez le projet `WmpAxLib`.  
  
3.  Dans le projet WmpAxLib, ajoutez une référence à l’assembly de lecteur Windows Media nommé wmp.dll.  
  
4.  Ouvrez le **boîte à outils**.  
  
5.  Avec le bouton droit dans le **boîte à outils**, puis cliquez sur **choisir des éléments de**.  
  
6.  Cliquez sur le **des composants COM** onglet, sélectionnez le **le lecteur Windows Media** contrôler, puis cliquez sur **OK**.  
  
     Le contrôle Windows Media Player est ajouté à la **boîte à outils**.  
  
7.  Dans l’Explorateur de solutions, cliquez sur le **UserControl1** de fichiers, puis cliquez sur **renommer**.  
  
8.  Remplacez le nom par `WmpAxControl.vb` ou `WmpAxControl.cs`, selon le langage.  
  
9. Si vous êtes invité à renommer toutes les références, cliquez sur **Oui**.  
  
## <a name="creating-the-activex-control"></a>Création du contrôle ActiveX  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]génère automatiquement un <xref:System.Windows.Forms.AxHost> classe wrapper pour un [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] contrôle lorsque le contrôle est ajouté à une aire de conception. La procédure suivante crée un assembly managé nommé AxInterop.WMPLib.dll.  
  
#### <a name="to-create-the-activex-control"></a>Pour créer le contrôle ActiveX  
  
1.  Ouvrez WmpAxControl.cs ou WmpAxControl.vb dans le Concepteur Windows Forms.  
  
2.  À partir de la **boîte à outils**, ajoutez le contrôle de lecteur Windows Media à l’aire de conception.  
  
3.  Dans la fenêtre Propriétés, définissez la valeur du contrôle Lecteur Windows Media <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.  
  
4.  Générez le projet de bibliothèque de contrôles WmpAxLib.  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hébergement du contrôle ActiveX sur une Page WPF  
  
#### <a name="to-host-the-activex-control"></a>Pour héberger le contrôle ActiveX  
  
1.  Dans le projet HostingAxInWpf, ajoutez une référence à généré [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] assembly d’interopérabilité.  
  
     Cet assembly est nommé AxInterop.WMPLib.dll et a été ajouté au dossier Debug du projet WmpAxLib lorsque vous avez importé le contrôle du lecteur Windows Media.  
  
2.  Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.  
  
3.  Ajoutez une référence à la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly nommé System.Windows.Forms.dll.  
  
4.  Ouvrez MainWindow.xaml dans le Concepteur WPF.  
  
5.  Nom de la <xref:System.Windows.Controls.Grid> élément `grid1`.  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  En mode Création ou la vue XAML, sélectionnez le <xref:System.Windows.Window> élément.  
  
7.  Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.  
  
8.  Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.  
  
9. Insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.  
  
     Ce code crée une instance de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôler et ajoute une instance de la `AxWindowsMediaPlayer` contrôle enfant.  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Appuyez sur F5 pour générer et exécuter l'application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Concepteur WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
