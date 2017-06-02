---
title: "Comment&#160;: lier le contr&#244;le DataGrid Windows Forms &#224; une source de donn&#233;es &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "contrôles dépendants"
  - "contrôles dépendants, DataGrid (contrôle)"
  - "liaison de données, DataGrid (contrôle)"
  - "contrôles liés aux données, DataGrid"
  - "DataGrid (contrôle Windows Forms), liaison de données"
  - "groupes de données (Windows Forms), lier au contrôle DataGrid"
  - "contrôles Windows Forms, liaison de données"
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: lier le contr&#244;le DataGrid Windows Forms &#224; une source de donn&#233;es &#224; l&#39;aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms est spécialement conçu pour afficher des informations d'une source de données.  Vous le liez au moment du design en définissant les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A>, ou au moment de l'exécution en appelant la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.  Bien que vous puissiez afficher des données provenant d'un large éventail de sources de données, les sources les plus courantes sont les groupes de données et les vues de données.  
  
 Si la source de données est disponible au moment du design \(par exemple si le formulaire contient une instance d'un groupe de données ou d'une vue de données\), vous pouvez lier la grille à cette source au même moment.  Il est possible d'afficher un aperçu de l'apparence qu'auront les données dans la grille.  
  
 Vous pouvez aussi lier la grille par programme, au moment de l'exécution.  Cela est utile lorsque vous voulez définir une source de données basée sur des informations obtenues au moment de l'exécution  \(par exemple, l'application peut permettre à l'utilisateur de spécifier le nom d'une table à afficher\).  En outre, cela est nécessaire lorsque la source n'existe pas au moment du design.  Ce peut être le cas de sources telles que tableaux, collections, groupes de données non typés et lecteurs de données.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGrid>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], par défaut, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils**.  Pour plus d'informations sur son ajout, consultez [How to: Add Items to the Toolbox](http://msdn.microsoft.com/fr-fr/458e119e-17fe-450b-b889-e31c128bd7e0).  Par ailleurs, dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], vous pouvez utiliser la fenêtre **Sources de données** pour la liaison de données au moment du design.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour lier les données du contrôle DataGrid à une table unique dans le concepteur  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> du contrôle l'objet contenant les éléments de données avec lesquels vous souhaitez établir une liaison.  
  
2.  Si la source de données est un groupe de données, affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A> le nom de la table avec laquelle établir une liaison.  
  
3.  Si la source est un groupe de données ou une vue de données basée sur une table de groupe de données, ajoutez au formulaire du code destiné à remplir le groupe de données.  
  
     Le code exact utilisé dépend de la provenance des données du groupe.  Si le groupe de données est rempli directement à partir d'une base de données, vous appelez en général la méthode `Fill` d'un adaptateur de données, comme dans l'exemple de code suivant, qui remplit le groupe de données `DsCategories1` :  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  \(Facultatif\) Ajoutez les styles de table et de colonne appropriés à la grille.  
  
     S'il n'existe pas de style de table, la table s'affichera avec une mise en forme minimale et toutes ses colonnes visibles.  
  
### Pour lier les données du contrôle DataGrid à plusieurs tables d'un groupe de données dans le concepteur  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> du contrôle l'objet contenant les éléments de données avec lesquels vous souhaitez établir une liaison.  
  
2.  Si le groupe de données contient des tables connexes \(c'est\-à\-dire s'il contient un objet de relation\), affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A> le nom de la table parente.  
  
3.  Écrivez le code servant à remplir le groupe de données.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Accès aux données dans Visual Studio](../Topic/Accessing%20data%20in%20Visual%20Studio.md)