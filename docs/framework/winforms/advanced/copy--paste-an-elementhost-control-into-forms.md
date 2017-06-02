---
title: "Proc&#233;dure pas &#224; pas&#160;: copier-coller d&#39;un contr&#244;le ElementHost dans d&#39;autres Windows Forms | Microsoft Docs"
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
  - "ElementHost (contrôle), copier et coller au moment du design"
  - "interopérabilité (WPF)"
  - "Windows Forms, copier et coller du contenu"
  - "WPF (contrôle utilisateur), héberger dans les Windows Forms"
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Proc&#233;dure pas &#224; pas&#160;: copier-coller d&#39;un contr&#244;le ElementHost dans d&#39;autres Windows Forms
Cette procédure pas à pas montre comment copier un contrôle Windows Presentation Foundation \(WPF\) d'un Windows Form à un autre.  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   copier un contrôle WPF.  
  
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
  
-   Créez un projet d'application Windows Forms dans Visual Basic ou Visual C\# nommé `CopyElementHost`.  
  
## Copie d'un contrôle WPF  
 Après avoir ajouté un contrôle WPF au projet, vous pouvez le copier vers d'autres formulaires du projet.  
  
#### Pour copier un contrôle WPF  
  
1.  Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.  Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.  Pour plus d'informations, consultez [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Générez le projet.  
  
3.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
4.  Faites glisser une instance de `UserControl1` de la **Boîte à outils** vers le formulaire.  
  
     Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
5.  `elementHost1` étant sélectionné, appuyez sur Ctrl\+C pour le copier dans le Presse\-papiers.  
  
6.  Ajoutez un nouveau Windows Form au projet.  Utilisez le nom par défaut pour le type de formulaire, `Form2`.  
  
7.  `Form2` étant ouvert dans le Concepteur Windows Forms, appuyez sur Ctrl\+V pour coller une copie de `elementHost1` sur le formulaire.  
  
     Le contrôle copié se nomme également `elementHost1`, car il s'agit d'un champ privé de la classe `Form2`.  Il n'existe aucune collision de nom avec le `elementHost1` dans la classe `Form1`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)