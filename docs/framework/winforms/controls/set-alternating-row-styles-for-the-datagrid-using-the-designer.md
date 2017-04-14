---
title: "Comment&#160;: d&#233;finir des styles de ligne en alternance pour le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "données (Windows Forms), afficher"
  - "DataGridView (contrôle Windows Forms), alternative de style de ligne"
  - "formats de type livre comptable"
  - "lignes, en alternance"
  - "Windows Forms, lignes"
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: d&#233;finir des styles de ligne en alternance pour le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Les données sous forme de tableau sont souvent présentées dans un format qui s'apparente à celui d'un registre où les lignes alternées ont des couleurs d'arrière\-plan différentes.  Avec ce format, il est plus facile pour les utilisateurs de déterminer les cellules de chaque ligne, surtout dans le cas de tableaux larges qui ont beaucoup de colonnes.  
  
 Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des informations de style complètes pour les lignes alternantes.  Vous pouvez utiliser des caractéristiques de style comme la couleur de premier plan et la police, en plus de la couleur d'arrière\-plan, différencier des lignes alternantes.  Pour plus d'informations, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Définir des styles pour les lignes alternantes  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.DataGridView> dans le concepteur.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>.  
  
3.  Dans la boîte de dialogue **Générateur CellStyle**, définissez le style en paramétrant les propriétés et utilisez le volet **Aperçu** pour confirmer vos choix.  Les styles que vous spécifiez sont utilisés pour chaque autre ligne affichée dans le contrôle, à partir de la deuxième.  
  
4.  Pour définir des styles pour les lignes restantes, répétez des étapes 2 et 3 à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.  
  
    > [!NOTE]
    >  Les cellules sont affichées à l'aide de styles hérités de plusieurs propriétés.  Pour plus d'informations sur l'héritage de style, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Utilisation du concepteur avec le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)