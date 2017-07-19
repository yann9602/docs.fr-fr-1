---
title: "Comment&#160;: d&#233;finir une colonne en lecture seule dans le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "colonnes (Windows Forms), en lecture seule"
  - "données (Windows Forms), afficher"
  - "DataGridView (contrôle Windows Forms), colonnes en lecture seule"
  - "Windows Forms, colonnes"
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: d&#233;finir une colonne en lecture seule dans le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Par défaut, les utilisateurs peuvent modifier le texte et les données numériques affichées dans le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>.  Si vous souhaitez afficher des données qui ne sont pas destinées à être modifiées, vous devez faire de la colonne qui contient ces données une colonne en lecture seule.  Pour plus d'informations sur la façon de rendre le contrôle entièrement en lecture seule, consultez [Comment : empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir une colonne en lecture seule à l'aide du concepteur  
  
1.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans l'angle supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la liste **Colonnes sélectionnées**.  
  
3.  Dans la grille **Propriétés des colonnes**, affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> la valeur `true`.  
  
    > [!NOTE]
    >  Vous pouvez également rendre une colonne en lecture seule lorsque vous l'ajoutez en activant la case à cocher **Lecture seule** dans la boîte de dialogue **Ajouter une colonne**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=fullName>   
 [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [Comment : empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)