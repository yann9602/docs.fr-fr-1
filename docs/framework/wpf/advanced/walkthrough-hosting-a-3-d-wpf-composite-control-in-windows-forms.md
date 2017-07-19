---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le composite&#160;3-D&#160;WPF dans les Windows Forms | Microsoft Docs"
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
  - "contrôles composites, héberger WPF dans"
  - "héberger un contenu WPF dans les Windows Forms"
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement d&#39;un contr&#244;le composite&#160;3-D&#160;WPF dans les Windows Forms
Cette procédure pas à pas montre comment vous pouvez créer un contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et l'héberger dans les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] en utilisant le contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  
  
 Dans cette procédure pas à pas, vous implémenterez un <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui contient deux contrôles enfants.  Le <xref:System.Windows.Controls.UserControl> affiche un cône tridimensionnel \(3D\).  Le rendu d'objets 3D est beaucoup plus facile avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qu'avec [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Il est donc normal d'héberger une classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> pour créer des graphiques 3D dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création du <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Création du projet hôte Windows Forms.  
  
-   Hébergement du <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pour obtenir l'intégralité du code de toutes les tâches illustrées dans cette procédure pas\-à\-pas, consultez [Hébergement d'un contrôle composite WPF 3D dans les Windows Forms, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160001).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## Création du contrôle utilisateur  
  
#### Pour créer le contrôle utilisateur  
  
1.  Créez un projet de bibliothèque de contrôles utilisateur WPF nommé `HostingWpfUserControlInWf`.  
  
2.  Ouvrez UserControl1.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
3.  Remplacez le code généré par le code suivant.  
  
     Ce code définit un <xref:System.Windows.Controls.UserControl?displayProperty=fullName> qui contient deux contrôles enfants.  Le premier contrôle enfant est un contrôle <xref:System.Windows.Controls.Label?displayProperty=fullName>; le deuxième est un <xref:System.Windows.Controls.Viewport3D> qui affiche un cône 3D.  
  
     [!code-xml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## Création du projet hôte Windows Forms  
  
#### Pour créer le projet hôte  
  
1.  Ajoutez un projet d'application Windows nommé `WpfUserControlHost` à la solution.  Pour plus d'informations, consultez [Comment : créer un projet d'application WPF](http://msdn.microsoft.com/fr-fr/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Dans l'explorateur de solutions, ajoutez une référence à l'assembly WindowsFormsIntegration nommé WindowsFormsIntegration.dll.  
  
3.  Ajoutez des références aux assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivants :  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  Ajoutez une référence au projet `HostingWpfUserControlInWf`.  
  
5.  Dans l'Explorateur de solutions, définissez le projet `WpfUserControlHost` comme le projet de démarrage.  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## Hébergement du contrôle utilisateur Windows Presentation Foundation  
  
#### Pour héberger le contrôle utilisateur  
  
1.  Dans le Concepteur Windows Forms, ouvrez Form1.  
  
2.  Dans la fenêtre Propriétés, cliquez sur **Événements**, puis double\-cliquez sur l'événement <xref:System.Windows.Forms.Form.Load> pour créer un gestionnaire d'événements.  
  
     L'éditeur de code ouvre le gestionnaire d'événements `Form1_Load` généré récemment.  
  
3.  Remplacez le code dans Form1.cs par le code suivant :  
  
     Le gestionnaire d'événements `Form1_Load` crée une instance de `UserControl1` et l'ajoute `` à la collection de contrôles enfants du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> est ajouté à la collection du formulaire des contrôles enfants.  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  Appuyez sur F5 pour générer et exécuter l'application.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Hébergement d'un contrôle composite WPF dans les Windows Forms, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160001)