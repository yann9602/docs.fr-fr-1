---
title: "Comment : créer des listes maître/détails avec le contrôle DataGrid Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1526a6e54078ea3dc0500c39a8fc2feda44d901
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Comment : créer des listes maître/détails avec le contrôle DataGrid Windows Forms à l'aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Si votre <xref:System.Data.DataSet> contient une série de tables connexes, vous pouvez utiliser deux <xref:System.Windows.Forms.DataGrid> contrôles pour afficher les données dans un format maître / détail. Un <xref:System.Windows.Forms.DataGrid> est désigné comme étant la grille principale, et la seconde est désignée comme étant la grille des détails. Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants connexes s’affichent dans la liste des détails. Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table connexe Orders, vous devez spécifier la table Customers pour la grille principale et la table Orders pour la grille de détails. Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders sont affichera dans la grille des détails.  
  
 La procédure suivante requiert un **Application Windows** projet. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Pour créer une liste maître / détails dans le Concepteur  
  
1.  Ajouter deux <xref:System.Windows.Forms.DataGrid> contrôles au formulaire. Pour plus d’informations, consultez [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], le <xref:System.Windows.Forms.DataGrid> contrôle n’est pas dans le **boîte à outils** par défaut. Pour plus d’informations, consultez [Comment : ajouter des éléments à la boîte à outils](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  Les étapes suivantes ne sont pas applicables aux [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], qui utilise le **des Sources de données** fenêtre pour la liaison de données au moment du design. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) et [Comment : afficher des données connexes dans une Application Windows Forms](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  Faites glisser deux ou plusieurs tables à partir de **l’Explorateur de serveurs** au formulaire.  
  
3.  À partir de la **données** menu, sélectionnez **générer le DataSet**.  
  
4.  Définir les relations entre les tables à l’aide du Concepteur XML. Pour plus d’informations, consultez « Comment : créer un-à-plusieurs relations dans les schémas XML et les jeux de données » sur MSDN.  
  
5.  Enregistrez les relations en sélectionnant **Enregistrer tout** à partir de la **fichier** menu.  
  
6.  Configurer la <xref:System.Windows.Forms.DataGrid> contrôle que vous souhaitez désigner comme grille principale, comme suit :  
  
    1.  Sélectionnez le <xref:System.Data.DataSet> dans la liste déroulante dans le <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété.  
  
    2.  Sélectionnez la table principale (par exemple, « Customers ») dans la liste déroulante dans le <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété.  
  
7.  Configurer la <xref:System.Windows.Forms.DataGrid> contrôle que vous souhaitez désigner la grille des détails, comme suit :  
  
    1.  Sélectionnez le <xref:System.Data.DataSet> dans la liste déroulante dans le <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété.  
  
    2.  Sélectionnez la relation (par exemple, « Customers.CustOrd ») entre les tables principale et détaillée dans la liste déroulante dans le <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété. Pour voir la relation, développez le nœud en cliquant sur le signe plus (**+**) en regard de la table principale dans la liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Vue d’ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
