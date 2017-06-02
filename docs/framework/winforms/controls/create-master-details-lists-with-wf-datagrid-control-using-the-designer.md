---
title: "Comment&#160;: cr&#233;er des listes ma&#238;tre/d&#233;tails avec le contr&#244;le DataGrid Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "DataGrid (contrôle Windows Forms), listes maître/détails"
  - "listes maître/détails"
  - "tables connexes, afficher dans le contrôle DataGrid"
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er des listes ma&#238;tre/d&#233;tails avec le contr&#244;le DataGrid Windows Forms &#224; l&#39;aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Si votre <xref:System.Data.DataSet> contient une série de tables connexes, vous pouvez utiliser deux contrôles <xref:System.Windows.Forms.DataGrid> pour afficher les données dans un format maître\/détails.  Le premier contrôle <xref:System.Windows.Forms.DataGrid> est désigné comme grille principale et le second comme grille détaillée.  Lorsque vous sélectionnez une entrée dans la liste maître, toutes les entrées enfants connexes s'affichent dans la liste détails.  Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table connexe Orders, vous spécifiez la table Customers comme grille principale et la table Orders comme grille détaillée.  Lorsqu'un client est sélectionné dans la grille principale, toutes les commandes qui lui sont associées dans la table Orders s'affichent dans la grille détaillée.  
  
 La procédure suivante nécessite un projet d'**application Windows**.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer une liste maître\/détails dans le concepteur  
  
1.  Ajoutez deux contrôles <xref:System.Windows.Forms.DataGrid> au formulaire.  Pour plus d'informations, consultez [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], par défaut, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils**.  Pour plus d'informations, consultez [How to: Add Items to the Toolbox](http://msdn.microsoft.com/fr-fr/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Les étapes suivantes ne sont pas applicables à [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], qui utilise la fenêtre **Sources de données** pour la liaison de données au moment du design.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md) et [Comment : afficher des données connexes dans une application Windows Forms](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md).  
  
2.  Faites glisser deux tables ou plus de l'**Explorateur de serveurs** vers le formulaire.  
  
3.  Dans le menu **Données**, sélectionnez **Générer le DataSet**.  
  
4.  Définissez les relations unissant les tables à l'aide du Concepteur XML.  Pour plus d'informations, consultez "Comment : créer des relations un\-à\-plusieurs dans des schémas XML et des groupes de données \(Concepteur XML\) sur MSDN.  
  
5.  Enregistrez les relations en cliquant sur **Enregistrer tout** dans le menu **Fichier**.  
  
6.  Configurez le contrôle <xref:System.Windows.Forms.DataGrid> que vous voulez désigner comme grille principale, en procédant comme suit :  
  
    1.  Sélectionnez <xref:System.Data.DataSet> dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A>.  
  
    2.  Sélectionnez la table principale \(par exemple « Customers »\) dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A>.  
  
7.  Configurez le contrôle <xref:System.Windows.Forms.DataGrid> que vous voulez désigner comme grille détaillée, en procédant comme suit :  
  
    1.  Sélectionnez <xref:System.Data.DataSet> dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A>.  
  
    2.  Sélectionnez la relation \(par exemple "Customers.CustOrd"\) unissant la table principale et les tables secondaires dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A>.  Pour voir s'afficher la relation, développez le nœud en cliquant sur le signe **\+** \(plus\) situé en regard de la table principale dans la liste déroulante.  
  
## Voir aussi  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Vue d'ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [Comment : lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [Liaison de contrôles à des données dans Visual Studio](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)