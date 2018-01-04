---
title: Vue d'ensemble de GridView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 099584ff5149891f406d5ad24a28a6b3e3faafb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gridview-overview"></a>Vue d'ensemble de GridView
<xref:System.Windows.Controls.GridView>mode d’affichage est un des modes d’affichage pour un <xref:System.Windows.Controls.ListView> contrôle. La <xref:System.Windows.Controls.GridView> classe et ses classes de prise en charge permettent aux administrateurs et les utilisateurs afficher des collections d’éléments dans une table qui utilise généralement des boutons comme en-têtes de colonnes interactifs. Cette rubrique présente la <xref:System.Windows.Controls.GridView> classe et décrit son utilisation.  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Qu’est-ce qu’un affichage de grille ou GridView ?  
 Le <xref:System.Windows.Controls.GridView> mode affiche une liste d’éléments de données par la liaison des champs de données à des colonnes et en affichant un en-tête de colonne pour identifier le champ de vue. La valeur par défaut <xref:System.Windows.Controls.GridView> style implémente des boutons comme en-têtes de colonne. À l’aide des boutons pour les en-têtes de colonne, vous pouvez implémenter des fonctionnalités d’interaction utilisateur importants ; par exemple, les utilisateurs sur l’en-tête de colonne pour trier <xref:System.Windows.Controls.GridView> données en fonction du contenu d’une colonne spécifique.  
  
> [!NOTE]
>  Les contrôles bouton que <xref:System.Windows.Controls.GridView> utilise pour les en-têtes de colonne est dérivés de <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.GridView> afficher de <xref:System.Windows.Controls.ListView> contenu.  
  
 **Affichage GridView de contenu ListView**  
  
 ![ListView mis en forme](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")  
  
 <xref:System.Windows.Controls.GridView>les colonnes sont représentées par <xref:System.Windows.Controls.GridViewColumn> objets dont la taille s’adapte automatiquement à leur contenu. Si vous le souhaitez, vous pouvez définir explicitement une <xref:System.Windows.Controls.GridViewColumn> à une largeur spécifique. Vous pouvez redimensionner les colonnes en faisant glisser la barre de redimensionnement entre les en-têtes de colonnes. Vous pouvez également dynamiquement ajouter, supprimer, remplacer et réorganiser les colonnes, car cette fonctionnalité est intégrée à <xref:System.Windows.Controls.GridView>. Toutefois, <xref:System.Windows.Controls.GridView> ne peut pas mettre à jour directement les données qu’il affiche.  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.GridView> qui affiche des données de l’employé. Dans cet exemple, <xref:System.Windows.Controls.ListView> définit le `EmployeeInfoDataSource` comme le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Les définitions de propriétés de <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> lier <xref:System.Windows.Controls.GridViewColumn> contenu `EmployeeInfoDataSource` des catégories de données.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre la table créée par l’exemple précédent.  
  
 **GridView qui affiche des données à partir de ItemsSource**  
  
 ![ListView avec sortie GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Disposition et style de GridView  
 Les cellules et l’en-tête de colonne d’un <xref:System.Windows.Controls.GridViewColumn> ont la même largeur. Par défaut, chaque colonne adapte sa largeur à son contenu. Si vous le souhaitez, vous pouvez définir une colonne sur une largeur fixe.  
  
 Le contenu des données connexes s’affiche sur des lignes horizontales. Par exemple, dans l’illustration précédente, le nom, le prénom et le numéro d’identification de chaque employé s’affichent en tant qu’ensemble parce qu’ils apparaissent dans une ligne horizontale.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Définir et appliquer un style aux colonnes dans GridView  
 Lorsque vous définissez le champ de données à afficher dans un <xref:System.Windows.Controls.GridViewColumn>, utilisez le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, ou <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> propriétés. Le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété est prioritaire sur une des propriétés du modèle.  
  
 Pour spécifier l’alignement du contenu dans une colonne d’un <xref:System.Windows.Controls.GridView>, définir un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. N’utilisez pas le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> et <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriétés <xref:System.Windows.Controls.ListView> contenu qui s’affiche à l’aide un <xref:System.Windows.Controls.GridView>.  
  
 Pour spécifier les propriétés de style et de modèle pour les en-têtes de colonne, utilisez la <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, et <xref:System.Windows.Controls.GridViewColumnHeader> classes. Pour plus d’informations, consultez [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Ajout d’éléments visuels à un affichage GridView  
 Pour ajouter des éléments visuels, tels que <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.Button> des contrôles, à un <xref:System.Windows.Controls.GridView> mode d’affichage, utilisez des modèles ou des styles.  
  
 Si vous définissez explicitement un élément visuel comme un élément de données, il peut apparaître qu’une seule fois dans un <xref:System.Windows.Controls.GridView>. Cette limitation existe parce qu’un élément ne peut avoir qu’un seul parent et par conséquent, ne peut apparaître qu’une seule fois dans l’arborescence visuelle.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Appliquer un style à des lignes dans un affichage GridView  
 Utilisez le <xref:System.Windows.Controls.GridViewRowPresenter> et <xref:System.Windows.Controls.GridViewHeaderRowPresenter> classes à mettre en forme et afficher les lignes d’un <xref:System.Windows.Controls.GridView>. Pour obtenir un exemple de style à des lignes dans un <xref:System.Windows.Controls.GridView> mode d’affichage, consultez [Style d’une ligne dans un ListView That Implements un GridView](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problèmes d’alignement lorsque vous utilisez ItemContainerStyle  
 Pour éviter les problèmes d’alignement entre les cellules et les en-têtes de colonne, ne définissez pas une propriété ou spécifier un modèle qui affecte la largeur d’un élément dans un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Par exemple, ne définissez pas le <xref:System.Windows.FrameworkElement.Margin%2A> propriété ou spécifiez un <xref:System.Windows.Controls.ControlTemplate> qui ajoute un <xref:System.Windows.Controls.CheckBox> à un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> qui est définie sur une <xref:System.Windows.Controls.ListView> contrôle. Au lieu de cela, spécifiez les propriétés et les modèles qui affectent la largeur de colonne directement sur les classes qui définissent un <xref:System.Windows.Controls.GridView> mode d’affichage.  
  
 Par exemple, pour ajouter un <xref:System.Windows.Controls.CheckBox> aux lignes de <xref:System.Windows.Controls.GridView> mode d’affichage, ajoutez le <xref:System.Windows.Controls.CheckBox> à un <xref:System.Windows.DataTemplate>, puis définissez le <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriété qui <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interactions utilisateur avec un affichage GridView  
 Lorsque vous utilisez un <xref:System.Windows.Controls.GridView> dans votre application, les utilisateurs peuvent interagir avec et modifier la mise en forme de la <xref:System.Windows.Controls.GridView>. Par exemple, les utilisateurs peuvent réorganiser les colonnes, redimensionner une colonne, sélectionner des éléments dans une table et faire défiler le contenu. Vous pouvez également définir un gestionnaire d’événements qui répond lorsqu’un utilisateur clique sur le bouton d’en-tête de colonne. Le Gestionnaire d’événements peut effectuer des opérations comme trier les données qui s’affiche dans le <xref:System.Windows.Controls.GridView> en fonction du contenu d’une colonne.  
  
 La liste suivante décrit plus en détail les fonctionnalités de l’utilisation de <xref:System.Windows.Controls.GridView> pour l’interaction de l’utilisateur :  
  
-   **Réorganiser les colonnes à l’aide de la méthode glisser-déplacer.**  
  
     Les utilisateurs peuvent réorganiser les colonnes dans un <xref:System.Windows.Controls.GridView> en appuyant sur le bouton gauche de la souris alors qu’il est sur un en-tête de colonne, puis en faisant glisser cette colonne vers une nouvelle position. Lorsque l’utilisateur fait glisser l’en-tête de colonne, une version flottante de l’en-tête s’affiche ainsi qu’une ligne noire unie qui indique où insérer la colonne.  
  
     Si vous souhaitez modifier le style par défaut de la version flottante d’un en-tête, spécifiez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.GridViewColumnHeader> type qui est déclenché lorsque la <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> est définie sur <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Pour plus d’informations, consultez [Créer un style pour un en-tête de colonne GridView déplacé](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
-   **Redimensionner une colonne selon son contenu.**  
  
     Les utilisateurs peuvent double-cliquer sur la barre de redimensionnement à droite d’un en-tête de colonne afin de redimensionner une colonne en fonction de son contenu.  
  
    > [!NOTE]
    >  Vous pouvez définir le <xref:System.Windows.Controls.GridViewColumn.Width%2A> propriété `Double.NaN` pour produire le même effet.  
  
-   **Sélectionner des éléments de lignes.**  
  
     Les utilisateurs peuvent sélectionner un ou plusieurs éléments dans un <xref:System.Windows.Controls.GridView>.  
  
     Si vous souhaitez modifier le <xref:System.Windows.Style> d’un élément sélectionné, consultez [utiliser des déclencheurs pour le Style des éléments sélectionnés dans un ListView](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
-   **Faire défiler pour afficher le contenu qui n’est pas initialement visible à l’écran.**  
  
     Si la taille de la <xref:System.Windows.Controls.GridView> est pas suffisamment grande pour afficher tous les éléments, les utilisateurs peuvent faire défiler horizontalement ou verticalement en utilisant les barres de défilement, qui sont fournis par un <xref:System.Windows.Controls.ScrollViewer> contrôle. A <xref:System.Windows.Controls.Primitives.ScrollBar> est masquée si tout le contenu est visible dans une orientation spécifique. Les en-têtes de colonnes ne défilent pas avec une barre de défilement verticale. Ils défilent horizontalement.  
  
-   **Interagir avec les colonnes en cliquant sur les boutons d’en-tête de colonne.**  
  
     Lorsque les utilisateurs cliquent sur un bouton d’en-tête de colonne, ils peuvent trier les données qui s’affichent dans la colonne si vous avez fourni un algorithme de tri.  
  
     Vous pouvez gérer le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événements pour les boutons d’en-tête de colonne pour fournir des fonctionnalités telles qu’un algorithme de tri. Pour gérer les <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour un en-tête de colonne unique, définissez un gestionnaire d’événements sur le <xref:System.Windows.Controls.GridViewColumnHeader>. Pour définir un gestionnaire d’événements qui gère la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événements pour tous les en-têtes de colonnes, définissez le gestionnaire sur le <xref:System.Windows.Controls.ListView> contrôle.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Obtention d’autres vues personnalisées  
 Le <xref:System.Windows.Controls.GridView> (classe), qui est dérivée de la <xref:System.Windows.Controls.ViewBase> classe abstraite, est qu’un des modes d’affichage possibles pour la <xref:System.Windows.Controls.ListView> classe. Vous pouvez créer d’autres vues personnalisées pour <xref:System.Windows.Controls.ListView> en dérivant de la <xref:System.Windows.Controls.ViewBase> classe. Pour obtenir un exemple de mode d’affichage personnalisé, consultez [Créer un mode d’affichage personnalisé pour un ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Classes de prise en charge pour GridView  
 Les classes suivantes prise en charge la <xref:System.Windows.Controls.GridView> mode d’affichage.  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Trier une colonne GridView lors d’un clic sur un en-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
