---
title: "Comment&#160;: modifier le type d&#39;une colonne DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "colonnes (Windows Forms), types"
  - "données (Windows Forms), afficher"
  - "DataGridView (contrôle Windows Forms), modifier le type de colonne"
  - "Windows Forms, colonnes"
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: modifier le type d&#39;une colonne DataGridView Windows Forms &#224; l&#39;aide du concepteur
Vous pouvez parfois souhaiter modifier le type d'une colonne qui a déjà été ajoutée à un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms.  Par exemple, vous pouvez vouloir modifier les types de quelques\-unes des colonnes qui sont générées automatiquement lorsque vous liez le contrôle à une source de données.  Ceci est utile lorsque la table que vous affichez a des colonnes qui contiennent des clés étrangères aux lignes dans une table connexe.  Dans ce cas, vous pouvez remplacer les colonnes de zone de texte qui affichent ces clés étrangères par les colonnes de zone de liste déroulante qui affichent des valeurs plus explicites de la table connexe.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour modifier le type d'une colonne à l'aide du concepteur  
  
1.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans l'angle supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la liste **Colonnes sélectionnées**.  
  
3.  Dans la grille **Propriétés des colonnes**, attribuez à la propriété `ColumnType` la valeur du nouveau type de colonne.  
  
    > [!NOTE]
    >  La propriété `ColumnType` est une propriété de moment de design uniquement qui indique la classe qui représente le type de colonne.  Il ne s'agit pas d'une propriété réelle définie dans une classe de colonne.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)