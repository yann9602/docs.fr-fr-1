---
title: "Comment&#160;: masquer les colonnes du contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "colonnes (Windows Forms), masquer"
  - "données (Windows Forms), afficher"
  - "DataGridView (contrôle Windows Forms), masquage de colonne"
  - "Windows Forms, colonnes"
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: masquer les colonnes du contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Quelquefois, vous souhaiterez afficher uniquement quelques\-unes des colonnes qui sont disponibles dans un contrôle Windows Forms<xref:System.Windows.Forms.DataGridView>.  Par exemple, vous pouvez vouloir montrer la colonne salaire d'un employé aux utilisateurs identifiés comme dirigeants tout en la masquant aux autres utilisateurs.  Sinon, vous pouvez lier le contrôle à une source de données qui contient beaucoup de colonnes dont vous ne voulez afficher qu'un certain nombre.  Dans ce cas, vous supprimerez en général les colonnes que vous ne voulez pas afficher plutôt que de les masquer.  Pour plus d'informations, consultez [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour masquer une colonne à l'aide du concepteur  
  
1.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans l'angle supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la liste **Colonnes sélectionnées**.  
  
3.  Dans la grille **Propriétés des colonnes**, affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> la valeur `false`.  
  
    > [!NOTE]
    >  Vous pouvez également masquer une colonne lors de son ajout en désactivant la case à cocher **Visible** dans la boîte de dialogue **Ajouter une colonne**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)