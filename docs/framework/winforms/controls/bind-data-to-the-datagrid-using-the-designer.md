---
title: "Comment&#160;: lier des donn&#233;es au contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "sources de données, lier à des contrôles Windows Forms"
  - "DataGridView (contrôle Windows Forms), liaison de données"
  - "contrôles Windows Forms, lier à une source de données"
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Comment&#160;: lier des donn&#233;es au contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Vous pouvez utiliser le concepteur pour connecter un contrôle <xref:System.Windows.Forms.DataGridView> aux sources de données de plusieurs types différents, y compris les bases de données, les objets métier ou les services Web.  Lorsque vous liez le contrôle à une source de données à l'aide du concepteur, le contrôle est lié automatiquement à un composant <xref:System.Windows.Forms.BindingSource> qui représente la source de données.  En outre, les colonnes sont générées automatiquement dans le contrôle pour correspondre aux informations de schéma fournies par la source de données.  
  
 Après avoir généré les colonnes, vous pouvez les modifier selon vos besoins.  Par exemple, vous pouvez supprimer ou masquer les colonnes que vous ne souhaitez pas afficher, vous pouvez réorganiser les colonnes ou vous pouvez modifier les types de colonne.  Pour plus d'informations sur la modification des colonnes, consultez les rubriques répertoriées dans la section Voir aussi.  
  
 Vous pouvez également lier plusieurs contrôles <xref:System.Windows.Forms.DataGridView> à des tables connexes afin de créer des relations maître\/détail.  Dans cette configuration, un contrôle affiche une table parente et un autre contrôle affiche uniquement les lignes d'une table enfant qui sont liées à ligne actuelle dans la table parente.  Pour plus d'informations, consultez [Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md).  
  
 La procédure suivante requiert un projet **Application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView> ou deux contrôles pour une relation maître\/détail.  Pour plus d'informations sur le lancement d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour lier le contrôle  à une source de données  
  
1.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
2.  Cliquez sur la flèche de déroulement pour l'option **Choisir la source de données**.  
  
3.  Si votre projet n'a pas déjà de source de données, cliquez sur **Ajouter la source de données du projet** et suivez les étapes indiquées par l'Assistant.  
  
     Pour plus d'informations, consultez [Configuration de source de données \(Assistant\)](../Topic/Data%20Source%20Configuration%20Wizard.md).  Votre nouvelle source de données apparaîtra dans la fenêtre déroulante  **Choisir la source de données**.  Si votre nouvelle source de données contient un seul membre, tel qu'une seule table de base de données, le contrôle crée automatiquement une liaison à ce membre.  Dans le cas contraire, passez à l'étape suivante.  
  
4.  Si ce n'est déjà fait, développez les nœuds **Autres sources de données** et **Sources de données du projet**, puis sélectionnez la source de données à laquelle lier le contrôle.  
  
5.  Si votre source de données contient plusieurs membres, comme lorsque vous avez créé un <xref:System.Data.DataSet?displayProperty=fullName> qui contient plusieurs tables, développez la source de données, puis sélectionnez le membre spécifique auquel lier le contrôle.  
  
6.  Pour créer une relation maître\/détail, dans la fenêtre déroulante **Choisir la source de données** d'un deuxième contrôle <xref:System.Windows.Forms.DataGridView>, développez le <xref:System.Windows.Forms.BindingSource> créé pour la table parente, puis sélectionnez la table enfant connexe dans la liste affichée.  
  
    > [!NOTE]
    >  Si votre projet possède déjà une source de données, vous pouvez également utiliser la fenêtre **Sources de données** pour créer un formulaire de données.  Pour plus d'informations, consultez [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 [Comment : établir une connexion à des données d'une base de données](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)   
 [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [Comment : modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)   
 [Comment : modifier le type d'une colonne DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)   
 [Comment : figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)   
 [Comment : masquer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)   
 [Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)