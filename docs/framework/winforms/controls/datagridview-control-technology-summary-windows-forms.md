---
title: "Résumé de la technologie du contrôle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e074229e4fe344633d277b77b6f7db881c154d8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Résumé de la technologie du contrôle DataGridView (Windows Forms)
Cette rubrique rassemble des informations sur le contrôle `DataGridView` et les classes qui prennent en charge son utilisation.  
  
 Affichage des données dans un format tabulaire est une tâche que vous êtes susceptible d’effectuer fréquemment. Le `DataGridView` contrôle est conçu pour être une solution complète pour la présentation des données dans une grille.  
  
## <a name="keywords"></a>Mots clés  
 DataGridView, BindingSource, table, cellule, liaison de données, mode virtuel  
  
## <a name="namespaces"></a>Espaces de noms  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Technologies associées  
 `BindingSource`  
  
## <a name="background"></a>Présentation  
 Concepteurs d’interface utilisateur utilisateur souvent s’avérer nécessaires pour afficher des données sous forme de tableau pour les utilisateurs. Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournit plusieurs façons d’afficher des données dans une table ou une grille. Le `DataGridView` contrôle représente l’évolution la plus récente de cette technologie pour les applications Windows Forms.  
  
 Le `DataGridView` contrôle peut afficher des lignes de données à partir d’un magasin de données. Plusieurs types de banques de données sont pris en charge. Le magasin de données peut contenir des données simples, non typées, par exemple, un tableau unidimensionnel, ou elle peut contenir des données typées, comme un <xref:System.Data.DataSet>. Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Le contrôle `DataGridView` offre un moyen puissant et flexible d'afficher des données sous forme de tableau. Vous pouvez utiliser le contrôle pour afficher des vues en lecture seule ou modifiables de petits ou très grands jeux de données.  
  
 Vous pouvez étendre la `DataGridView` contrôle de plusieurs façons pour générer un comportement personnalisé dans vos applications. Par exemple, vous pouvez spécifier par programmation vos propres algorithmes de tri et vous pouvez créer vos propres types de cellules. Vous pouvez facilement personnaliser l'apparence du contrôle `DataGridView` en choisissant parmi plusieurs propriétés. Nombreux types de magasins de données peuvent être utilisés comme source de données, ou le `DataGridView` contrôle peut fonctionner sans source de données qui lui est associée.  
  
## <a name="implementing-datagridview-classes"></a>Implémentation de Classes DataGridView  
 Il existe plusieurs façons pour vous permettre de tirer parti de la `DataGridView` fonctionnalités d’extensibilité du contrôle. Vous pouvez personnaliser de nombreux aspects du contrôle via les propriétés et événements, mais certaines personnalisations nécessitent que vous permet de créer de nouvelles classes dérivées d’existant `DataGridView` classes.  
  
 Les classes de base plus fréquemment utilisées sont `DataGridViewCell` et `DataGridViewColumn`. Vous pouvez dériver votre propre classe de cellule de `DataGridViewCell` ou l’une de ses classes enfants. Bien que vous pouvez ajouter n’importe quel type de cellule à n’importe quelle colonne, vous serez également généralement dériver une classe de colonne auxiliaire à partir de `DataGridViewColumn` qui héberge des cellules de votre type de cellule personnalisé par défaut.  
  
 Vous pouvez implémenter la `IDataGridViewEditingCell` interface dans votre classe de cellule dérivée pour créer un type de cellule qui dispose de fonctionnalités d’édition, mais n’héberge pas un contrôle en mode édition. Pour créer un contrôle que vous pouvez héberger dans une cellule en mode édition, vous pouvez implémenter la `IDataGridViewEditingControl` interface dans une classe dérivée de <xref:System.Windows.Forms.Control>.  
  
 Pour plus d’informations, consultez [Comment : personnaliser des cellules et des colonnes dans le contrôle DataGridView Windows Forms à l’apparence et le comportement de leur extension](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) et [Comment : héberger des contrôles dans les cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Classes DataGridView en un clin de œil  
 <xref:System.Windows.Forms>  
  
|Zone technologique|Classes/interfaces/éléments de configuration|  
|---------------------|-------------------------------------------------|  
|Liaison de données|<xref:System.Windows.Forms.BindingSource>|  
|Présentation des données|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell>et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewRow>et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn>et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView>Extensibilité|<xref:System.Windows.Forms.DataGridViewCell>et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn>et classes dérivées<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Nouveautés  
 Le <xref:System.Windows.Forms.DataGridView> contrôle est conçu pour être une solution complète pour l’affichage des données tabulaires avec Windows Forms. Vous devez envisager d’utiliser le <xref:System.Windows.Forms.DataGridView> de contrôle avant d’autres solutions, telles que <xref:System.Windows.Forms.DataGrid>, lorsque vous êtes en train de créer une nouvelle application. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle peut fonctionner en étroite collaboration avec le <xref:System.Windows.Forms.BindingSource> composant. Ce composant est conçu pour être la source de données principale d’un formulaire. Il peut gérer l’interaction entre une <xref:System.Windows.Forms.DataGridView> type de source de contrôle et sa source de données, quel que soit les données.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)
