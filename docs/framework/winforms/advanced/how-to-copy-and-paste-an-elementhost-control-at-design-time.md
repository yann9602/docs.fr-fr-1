---
title: "Comment&#160;: copier et coller un contr&#244;le ElementHost au moment du design | Microsoft Docs"
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
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: copier et coller un contr&#244;le ElementHost au moment du design
Cette procédure vous indique comment copier un contrôle WPF \(Windows Presentation Foundation\) sur un Windows Form.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour copier et coller un contrôle ElementHost au moment du design  
  
1.  Ajoutez un nouveau WPF <xref:System.Windows.Controls.UserControl> à votre projet Windows Forms.  Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.  Pour plus d'informations, consultez [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Dans la fenêtre **Propriétés**, affectez aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de `UserControl1` la valeur `200`.  
  
3.  Affectez la valeur `Bleu` à la propriété <xref:System.Windows.Controls.Control.Background%2A>.  
  
4.  Générez le projet.  
  
5.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
6.  Dans la **Boîte à outils**, faites glisser une instance de `UserControl1` sur le formulaire.  
  
     L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
7.  Après avoir sélectionné `elementHost1`, appuyez sur CTRL\+C pour le copier vers le Presse\-papiers.  
  
8.  Appuyez sur CTRL\+V pour coller le contrôle copié sur le formulaire.  
  
     Un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost2` est créé sur le formulaire.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Procédure pas à pas : copier\-coller d'un contrôle ElementHost dans d'autres Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)