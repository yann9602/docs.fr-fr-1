---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le ActiveX dans WPF | Microsoft Docs"
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
  - "contrôles ActiveX (interopérabilité WPF)"
  - "héberger des contrôles ActiveX"
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le ActiveX dans WPF
Pour permettre une interaction améliorée avec les navigateurs, vous pouvez utiliser des contrôles [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] dans votre application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Cette procédure pas à pas montre comment vous pouvez héberger le [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] en tant que contrôle sur une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   création du projet ;  
  
-   Création du contrôle ActiveX.  
  
-   Hébergement du contrôle ActiveX sur une page WPF.  
  
 Lorsque vous aurez complété cette procédure pas à pas, vous comprendrez comment utiliser des contrôles [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] dans votre application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] installé sur l'ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## Création du projet  
  
#### Pour créer et paramétrer le projet  
  
1.  Créez un projet d'application WPF nommé `HostingAxInWpf`.  
  
2.  Ajoutez un projet de bibliothèque de contrôles Windows Forms à la solution, puis nommez le projet `WmpAxLib`.  
  
3.  Dans le projet WmpAxLib, ajoutez une référence à l'assembly de Lecteur Windows Media nommé wmp.dll.  
  
4.  Ouvrez la **Boîte à outils**.  
  
5.  Cliquez avec le bouton droit sur **Boîte à outils**, puis cliquez sur **Choisir les éléments**.  
  
6.  Cliquez sur l'onglet **Composants COM**, sélectionnez le contrôle **Lecteur Windows Media**, puis cliquez sur **OK**.  
  
     Le contrôle de Lecteur Windows Media est ajouté à la **Boîte à outils**.  
  
7.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le fichier **UserControl1**, puis cliquez sur **Renommer**.  
  
8.  Modifiez le nom en `WmpAxControl.vb` ou `WmpAxControl.cs`, selon le langage.  
  
9. Si vous êtes invités à renommer toutes les références, cliquez sur **Oui**.  
  
## Création du contrôle ActiveX  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] génère automatiquement une classe wrapper <xref:System.Windows.Forms.AxHost> pour un contrôle [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] lorsque le contrôle est ajouté à une aire de conception.  La procédure suivante crée un assembly managé nommé AxInterop.WMPLib.dll.  
  
#### Pour créer le contrôle ActiveX  
  
1.  Ouvrez WmpAxControl.cs ou WmpAxControl.vb dans le Concepteur Windows Forms.  
  
2.  Dans la **Boîte à outils**, ajoutez le contrôle de Lecteur Windows Media à l'aire de conception.  
  
3.  Dans la fenêtre Propriétés, attribuez la valeur <xref:System.Windows.Forms.DockStyle> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle du Lecteur Windows Media.  
  
4.  Générez le projet de bibliothèque de contrôles WmpAxLib.  
  
## Hébergement du contrôle ActiveX sur une page WPF  
  
#### Pour héberger le contrôle ActiveX  
  
1.  Dans le projet HostingAxInWpf, ajoutez une référence à l'assembly d'interopérabilité [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] généré.  
  
     Cet assembly est nommé AxInterop.WMPLib.dll et a été ajouté au dossier Debug du projet WmpAxLib lorsque vous avez importé le contrôle du Lecteur Windows Media.  
  
2.  Ajoutez une référence à l'assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.  
  
3.  Ajoutez une référence à l'assembly [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nommé System.Windows.Forms.dll.  
  
4.  Ouvrez MainWindow.xaml dans le Concepteur WPF.  
  
5.  Nommez l'élément <xref:System.Windows.Controls.Grid> `grid1`.  
  
     [!code-xml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  En mode Design ou XAML, sélectionnez l'élément <xref:System.Windows.Window>.  
  
7.  Dans la fenêtre Propriétés, cliquez sur l'onglet **Événements**.  
  
8.  Double\-cliquez sur l'événement <xref:System.Windows.FrameworkElement.Loaded>.  
  
9. Insérez le code suivant pour gérer l'événement <xref:System.Windows.FrameworkElement.Loaded>.  
  
     Ce code crée une instance du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> et ajoute une instance du contrôle `AxWindowsMediaPlayer` en tant qu'enfant.  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Appuyez sur F5 pour générer et exécuter l'application.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)