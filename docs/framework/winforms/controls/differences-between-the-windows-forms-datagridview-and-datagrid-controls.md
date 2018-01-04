---
title: "Différences entre les contrôles DataGridView et DataGrid Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bc6d1fa2450d0aba52bd6a5a030c025fede0cb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Différences entre les contrôles DataGridView et DataGrid Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle est un nouveau contrôle qui remplace le <xref:System.Windows.Forms.DataGrid> contrôle. Le <xref:System.Windows.Forms.DataGridView> contrôle fournit de nombreuses fonctionnalités de base et avancées qui sont manquantes dans le <xref:System.Windows.Forms.DataGrid> contrôle. En outre, l’architecture de la <xref:System.Windows.Forms.DataGridView> contrôle rend beaucoup plus facile étendre et personnaliser à le <xref:System.Windows.Forms.DataGrid> contrôle.  
  
 Le tableau suivant décrit quelques-unes des fonctionnalités principales disponibles dans le <xref:System.Windows.Forms.DataGridView> contrôle sont absents de la <xref:System.Windows.Forms.DataGrid> contrôle.  
  
|Fonctionnalités du contrôle DataGridView|Description|  
|----------------------------------|-----------------|  
|Plusieurs types de colonne|Le <xref:System.Windows.Forms.DataGridView> contrôle fournit des types de colonne intégré plus que le <xref:System.Windows.Forms.DataGrid> contrôle. Ces types de colonnes selon les besoins de scénarios les plus courants, mais sont également plus faciles à étendre ou remplacer que les types de colonne dans la <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations, consultez [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs méthodes pour afficher des données|Le <xref:System.Windows.Forms.DataGrid> contrôle est limité à l’affichage des données à partir de la source de données externe. Le <xref:System.Windows.Forms.DataGridView> (contrôle), peut toutefois afficher des données indépendantes stockées dans le contrôle, des données à partir d’une source de données liée ou données dépendantes et indépendantes ensemble. Vous pouvez également implémenter le mode virtuel dans le <xref:System.Windows.Forms.DataGridView> contrôle pour fournir la gestion de données personnalisée. Pour plus d’informations, consultez [Modes d’affichage de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs façons de personnaliser l’affichage des données|Le <xref:System.Windows.Forms.DataGridView> contrôle fournit de nombreuses propriétés et événements qui vous permettent de spécifier comment les données sont mises en forme et affichées. Par exemple, vous pouvez modifier l’apparence des cellules, lignes et colonnes en fonction des données qu’ils contiennent, ou vous pouvez remplacer les données d’un type de données avec des données équivalent d’un autre type. Pour plus d’informations, consultez [mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs options pour modifier le comportement et l’apparence des cellules, lignes, colonnes et en-tête|Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet d’utiliser des composants de grille individuels de plusieurs façons. Par exemple, vous pouvez figer des lignes et des colonnes pour les empêcher de défilement ; masquer des lignes, colonnes et en-têtes ; modifier la façon dont les tailles d’en-tête de ligne et colonne sont ajustées. modifier la façon dont les utilisateurs effectuent des sélections ; et fournir des info-bulles et des menus contextuels pour les colonnes, lignes et cellules individuelles.|  
  
 Le <xref:System.Windows.Forms.DataGrid> contrôle est conservé pour la compatibilité descendante et pour des besoins particuliers. Pour presque tous les besoins, vous devez utiliser le <xref:System.Windows.Forms.DataGridView> contrôle. La seule fonctionnalité qui est disponible dans le <xref:System.Windows.Forms.DataGrid> contrôle qui n’est pas disponible dans le <xref:System.Windows.Forms.DataGridView> contrôle est l’affichage hiérarchique des informations à partir de deux tables connexes dans un seul contrôle. Vous devez utiliser deux <xref:System.Windows.Forms.DataGridView> contrôles pour afficher des informations à partir de deux tables qui ont une relation maître/détail.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Mise à niveau vers le contrôle DataGridView  
 Si vous avez des applications existantes qui utilisent le <xref:System.Windows.Forms.DataGrid> contrôle dans un scénario simple lié aux données sans personnalisations, vous pouvez simplement remplacer l’ancien contrôle avec le nouveau contrôle. Les deux contrôles utilisent l’architecture de liaison de données Windows Forms standard, donc la <xref:System.Windows.Forms.DataGridView> contrôle affiche vos données liées sans aucune configuration supplémentaire requise. Vous souhaiterez peut-être tirer parti des améliorations de liaison de données, cependant, en liant vos données à un <xref:System.Windows.Forms.BindingSource> composant, vous pouvez ensuite lier la <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations, consultez [composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Étant donné que la <xref:System.Windows.Forms.DataGridView> contrôle possède une architecture entièrement nouvelle, il n’existe aucun chemin d’accès de conversion simple qui vous permettra d’utiliser <xref:System.Windows.Forms.DataGrid> personnalisations avec les <xref:System.Windows.Forms.DataGridView> contrôle. Nombreux <xref:System.Windows.Forms.DataGrid> les personnalisations sont inutiles avec le <xref:System.Windows.Forms.DataGridView> contrôler, toutefois, en raison des fonctionnalités intégrées disponibles dans le nouveau contrôle. Si vous avez créé des types de colonnes personnalisés pour le <xref:System.Windows.Forms.DataGrid> contrôle que vous souhaitez utiliser avec le <xref:System.Windows.Forms.DataGridView> (contrôle), vous devez les implémenter en utilisant la nouvelle architecture. Pour plus d’informations, consultez [personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [BindingSource, composant](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Modes de tri des colonnes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
