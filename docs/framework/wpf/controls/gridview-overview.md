---
title: "Vue d&#39;ensemble de GridView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles, ListView"
  - "GridView (mode d'affichage)"
  - "contrôles ListView, GridView (mode d'affichage)"
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Vue d&#39;ensemble de GridView
Le mode d'affichage <xref:System.Windows.Controls.GridView> est l'un des modes d'affichage d'un contrôle <xref:System.Windows.Controls.ListView>.  La classe <xref:System.Windows.Controls.GridView> et ses classes de prise en charge vous permettent, à vous et à vos utilisateurs, de voir des collections d'éléments dans une table qui utilise généralement des boutons comme en\-têtes de colonnes interactifs.  Cette rubrique introduit la classe <xref:System.Windows.Controls.GridView> et décrit son utilisation.  
  
   
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## Qu'est\-ce qu'une vue GridView ?  
 Le mode d'affichage <xref:System.Windows.Controls.GridView> affiche une liste des éléments de données en liant des champs de données à des colonnes et en affichant un en\-tête de colonne pour identifier le champ.  Le style <xref:System.Windows.Controls.GridView> par défaut implémente des boutons comme en\-têtes de colonnes.  En utilisant des boutons comme en\-têtes de colonnes, vous pouvez implémenter d'importantes fonctionnalités d'interaction avec l'utilisateur. Par exemple, les utilisateurs peuvent cliquer sur l'en\-tête de colonne pour trier des données <xref:System.Windows.Controls.GridView> d'après le contenu d'une colonne spécifique.  
  
> [!NOTE]
>  Les contrôles bouton que <xref:System.Windows.Controls.GridView> utilise comme en\-têtes de colonnes sont dérivés de <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 L'illustration suivante montre une vue <xref:System.Windows.Controls.GridView> du contenu <xref:System.Windows.Controls.ListView>.  
  
 **Vue GridView d'un contenu ListView**  
  
 ![Vue de la liste mise en forme avec des styles](../../../../docs/framework/wpf/controls/media/styledlistview.png "StyledListView")  
  
 Les colonnes <xref:System.Windows.Controls.GridView> sont représentées par des objets <xref:System.Windows.Controls.GridViewColumn>, dont la taille s'adapte automatiquement à leur contenu.  Vous pouvez éventuellement affecter explicitement une largeur spécifique à <xref:System.Windows.Controls.GridViewColumn>.  Vous pouvez redimensionner des colonnes en faisant glisser la pince entre les en\-têtes de colonnes.  Vous pouvez également ajouter, supprimer, remplacer et réorganiser dynamiquement des colonnes, car ces fonctionnalités sont intégrées dans <xref:System.Windows.Controls.GridView>.  Toutefois, <xref:System.Windows.Controls.GridView> ne peut pas directement mettre à jour les données qu'il affiche.  
  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.GridView> qui affiche des données d'employé.  Dans cet exemple, <xref:System.Windows.Controls.ListView> définit `EmployeeInfoDataSource` comme <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>.  Les définitions de propriété de <xref:System.Windows.Controls.GridViewColumn> lient le contenu <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> aux catégories de données `EmployeeInfoDataSource`.  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L'illustration suivante montre la table créée par l'exemple précédent.  
  
 **GridView qui affiche des données à partir d'un ItemsSource**  
  
 ![Sortie de ListView avec GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## Disposition et style de GridView  
 Les cellules et l'en\-tête de colonne d'un <xref:System.Windows.Controls.GridViewColumn> ont la même largeur.  Par défaut, chaque colonne adapte sa largeur à son contenu.  Vous pouvez éventuellement affecter une largeur fixe à une colonne.  
  
 Le contenu des données connexes s'affiche dans les lignes horizontales.  Par exemple, dans l'illustration précédente, le nom, le prénom et le matricule de chaque employé s'affichent comme un jeu, parce qu'ils apparaissent dans une ligne horizontale.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### Définition et application d'un style de colonnes dans un GridView  
 Lorsque vous définissez le champ de données à afficher dans un <xref:System.Windows.Controls.GridViewColumn>, utilisez les propriétés <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> ou <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>.  La propriété <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> est prioritaire sur l'une ou l'autre des propriétés de modèle.  
  
 Pour spécifier l'alignement du contenu d'une colonne d'un <xref:System.Windows.Controls.GridView>, définissez un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  N'utilisez pas les propriétés <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> et <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> pour le contenu <xref:System.Windows.Controls.ListView> affiché à l'aide d'un <xref:System.Windows.Controls.GridView>.  
  
 Pour spécifier les propriétés de modèle et de style des en\-têtes de colonnes, utilisez les classes <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> et <xref:System.Windows.Controls.GridViewColumnHeader>.  Pour plus d'informations, consultez [Vue d'ensemble des modèles et styles d'en\-tête de colonne GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### Ajout d'éléments visuels à un GridView  
 Pour ajouter des éléments visuels, tels que des contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.Button>, à un mode d'affichage <xref:System.Windows.Controls.GridView>, utilisez des modèles ou des styles.  
  
 Si vous définissez explicitement un élément visuel comme élément de données, il ne peut apparaître qu'une seule fois dans un <xref:System.Windows.Controls.GridView>.  Cette limitation existe parce qu'un élément ne peut avoir qu'un seul parent et ne peut dès lors apparaître qu'une seule fois dans l'[arborescence visuelle](GTMT).  
  
<a name="StylingRowsinaGridViewView"></a>   
### Application d'un style à des lignes dans un GridView  
 Utilisez les classes <xref:System.Windows.Controls.GridViewRowPresenter> et <xref:System.Windows.Controls.GridViewHeaderRowPresenter> pour mettre en forme et afficher les lignes d'un <xref:System.Windows.Controls.GridView>.  Pour obtenir un exemple sur la manière d'appliquer un style à des lignes dans un mode d'affichage <xref:System.Windows.Controls.GridView>, consultez [Appliquer un style à une ligne dans un ListView implémentant un GridView](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### Problèmes d'alignement lorsque vous utilisez ItemContainerStyle  
 Pour éviter tout problème d'alignement entre en\-têtes et cellules de colonne, ne définissez pas de propriété ou ne spécifiez pas de modèle qui affecte la largeur d'un élément dans un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>.  Par exemple, ne définissez pas la propriété <xref:System.Windows.FrameworkElement.Margin%2A> ou ne spécifiez pas de <xref:System.Windows.Controls.ControlTemplate> qui ajoute un <xref:System.Windows.Controls.CheckBox> à un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> défini sur un contrôle <xref:System.Windows.Controls.ListView>.  À la place, spécifiez les propriétés et les modèles qui affectent directement la largeur de colonne aux classes qui définissent un mode d'affichage <xref:System.Windows.Controls.GridView>.  
  
 Par exemple, pour ajouter un <xref:System.Windows.Controls.CheckBox> aux lignes en mode d'affichage <xref:System.Windows.Controls.GridView>, ajoutez le <xref:System.Windows.Controls.CheckBox> à un <xref:System.Windows.DataTemplate>, puis affectez la propriété <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> à ce <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## Interactions utilisateur avec un GridView  
 Lorsque vous utilisez un <xref:System.Windows.Controls.GridView> dans votre application, les utilisateurs peuvent interagir avec et modifier la mise en forme du <xref:System.Windows.Controls.GridView>.  Par exemple, les utilisateurs peuvent réorganiser des colonnes, redimensionner une colonne, sélectionner des éléments dans une table et faire défiler le contenu.  Vous pouvez également définir un gestionnaire d'événements qui répond lorsqu'un utilisateur clique sur le bouton d'en\-tête de colonne.  Le gestionnaire d'événements peut effectuer des opérations comme trier les données affichées dans le <xref:System.Windows.Controls.GridView> d'après le contenu d'une colonne.  
  
 La liste suivante aborde dans plus de détail les fonctions de <xref:System.Windows.Controls.GridView> pour l'interaction avec l'utilisateur :  
  
-   **Réorganiser des colonnes à l'aide de la méthode du glisser\-déplacer.**  
  
     Les utilisateurs peuvent réorganiser des colonnes dans un <xref:System.Windows.Controls.GridView> en appuyant sur le bouton gauche de la souris lorsque le pointeur se trouve sur un en\-tête de colonne et en faisant ensuite glisser cette colonne vers une nouvelle position.  Lorsque l'utilisateur fait glisser l'en\-tête de colonne, une version flottante de l'en\-tête s'affiche ainsi qu'une ligne noire unie qui indique où insérer la colonne.  
  
     Pour modifier le style par défaut de la version flottante d'un en\-tête, spécifiez un <xref:System.Windows.Controls.ControlTemplate> pour un type <xref:System.Windows.Controls.GridViewColumnHeader> qui est déclenché lorsque la propriété <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> a la valeur <xref:System.Windows.Controls.GridViewColumnHeaderRole>.  Pour plus d'informations, consultez [Créer un style pour un en\-tête de colonne GridView déplacé](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
-   **Redimensionner une colonne selon son contenu.**  
  
     Les utilisateurs peuvent double\-cliquer sur la pince située à droite d'un en\-tête de colonne afin de redimensionner une colonne en fonction de son contenu.  
  
    > [!NOTE]
    >  Vous pouvez affecter la valeur `Double.NaN` à la propriété <xref:System.Windows.Controls.GridViewColumn.Width%2A> pour produire le même effet.  
  
-   **Sélectionner des éléments de ligne.**  
  
     Les utilisateurs peuvent sélectionner un ou plusieurs éléments dans un <xref:System.Windows.Controls.GridView>.  
  
     Pour modifier le <xref:System.Windows.Style> d'un élément sélectionné, consultez [Utiliser des déclencheurs pour appliquer un style aux éléments sélectionnés d'un ListView](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
-   **Faire défiler pour consulter le contenu qui n'est pas initialement visible à l'écran.**  
  
     Si le <xref:System.Windows.Controls.GridView> n'est pas assez grand pour afficher tous les éléments, les utilisateurs peuvent faire défiler horizontalement ou verticalement en utilisant des barres de défilement, fournies par un contrôle <xref:System.Windows.Controls.ScrollViewer>.  Une <xref:System.Windows.Controls.Primitives.ScrollBar> est masquée si tout le contenu est visible dans un sens spécifique.  Vous ne pouvez pas faire défiler des en\-têtes de colonnes verticalement mais bien horizontalement.  
  
-   **Interagir avec des colonnes en cliquant sur les boutons d'en\-tête de colonne.**  
  
     Lorsque les utilisateurs cliquent sur un bouton d'en\-tête de colonne, ils peuvent trier les données affichées dans la colonne si vous avez fourni un algorithme de tri.  
  
     Vous pouvez gérer l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour les boutons d'en\-tête de colonne afin de fournir des fonctionnalités telles qu'un algorithme de tri.  Pour gérer l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour un en\-tête de colonne unique, définissez un gestionnaire d'événements dans le <xref:System.Windows.Controls.GridViewColumnHeader>.  Pour définir un gestionnaire d'événements qui gère l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour tous les en\-têtes de colonnes, définissez le gestionnaire sur le contrôle <xref:System.Windows.Controls.ListView>.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## Obtention d'autres vues personnalisées  
 La classe <xref:System.Windows.Controls.GridView>, dérivée de la classe abstraite <xref:System.Windows.Controls.ViewBase> n'est que l'un des modes d'affichage possibles pour la classe <xref:System.Windows.Controls.ListView>.  Vous pouvez créer d'autres vues personnalisées pour <xref:System.Windows.Controls.ListView> en dérivant de la classe <xref:System.Windows.Controls.ViewBase>.  Pour obtenir un exemple de mode d'affichage personnalisé, consultez [Créer un mode d'affichage personnalisé pour un ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## Classes de prises en charge du GridView  
 Les classes suivantes prennent en charge le mode d'affichage <xref:System.Windows.Controls.GridView>.  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.ListViewItem>   
 <xref:System.Windows.Controls.GridViewColumn>   
 <xref:System.Windows.Controls.GridViewColumnHeader>   
 <xref:System.Windows.Controls.GridViewRowPresenter>   
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>   
 <xref:System.Windows.Controls.ViewBase>   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Trier une colonne GridView lors d'un clic sur un en\-tête](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)