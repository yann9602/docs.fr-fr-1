---
title: "Proc&#233;dure pas &#224; pas&#160;: modification des propri&#233;t&#233;s d&#39;un &#233;l&#233;ment WPF h&#233;berg&#233; au moment du design | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "interopérabilité (WPF)"
  - "Windows Forms, modifier des propriétés de contenu WPF au moment du design"
  - "contenu WPF (Windows Forms), modifier des propriétés au moment du design"
  - "contenu WPF, héberger dans les Windows Forms"
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Proc&#233;dure pas &#224; pas&#160;: modification des propri&#233;t&#233;s d&#39;un &#233;l&#233;ment WPF h&#233;berg&#233; au moment du design
Cette procédure pas à pas montre comment modifier les valeurs de propriétés d'un contrôle Windows Presentation Foundation \(WPF\) hébergé sur un Windows Form.  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer le contrôle WPF ;  
  
-   héberger les contrôles WPF sur un Windows Form ;  
  
-   utiliser le Concepteur WPF pour Visual Studio pour modifier les valeurs de propriétés.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C\# sont pris en charge.  
  
#### Pour créer le projet  
  
-   Créez un projet d'application Windows Forms dans Visual Basic ou Visual C\# nommé `WpfHost`.  
  
## Création du contrôle WPF  
 Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.  
  
#### Pour créer des contrôles WPF  
  
1.  Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet.  Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.  Pour plus d'informations, consultez [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Blue`.  
  
3.  Générez le projet.  
  
## Modification de valeurs de propriétés sur le contrôle WPF  
 Le Smart Tag <xref:System.Windows.Forms.Integration.ElementHost> facilite la modification des propriétés du contenu WPF hébergé à l'aide du Concepteur WPF.  
  
#### Pour héberger un contrôle WPF  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans la **Boîte à outils**, sous l'onglet **Contrôles utilisateur WPF**, double\-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.  
  
     L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
3.  Dans le panneau de Smart Tags **Tâches ElementHost**, sélectionnez **Modifier le contenu hébergé**.  
  
     UserControl1.xaml s'ouvre dans le Concepteur WPF.  
  
4.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Red`.  
  
5.  Regénérez le projet.  
  
6.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
     L'instance de `UserControl1` possède un arrière\-plan rouge.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Comment : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [Comment : aligner un contrôle sur les bords des formulaires au moment du design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)