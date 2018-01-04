---
title: Vue d'ensemble de Table
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 922faa06456a1aa86ffd0c805ab33577280ccf4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="table-overview"></a><span data-ttu-id="92206-102">Vue d'ensemble de Table</span><span class="sxs-lookup"><span data-stu-id="92206-102">Table Overview</span></span>
<span data-ttu-id="92206-103"><xref:System.Windows.Documents.Table>est un élément de niveau bloc qui prend en charge la présentation grille du contenu de document de flux.</span><span class="sxs-lookup"><span data-stu-id="92206-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="92206-104">La flexibilité de cet élément est très utile, mais rend plus difficiles sa compréhension et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="92206-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="92206-105">Cette rubrique contient les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="92206-105">This topic contains the following sections.</span></span>  
  
-   [<span data-ttu-id="92206-106">Principes de base de l’élément Table</span><span class="sxs-lookup"><span data-stu-id="92206-106">Table Basics</span></span>](#table_basics)  
  
-   [<span data-ttu-id="92206-107">Différences entre l’élément Table et l’élément Grid</span><span class="sxs-lookup"><span data-stu-id="92206-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
-   [<span data-ttu-id="92206-108">Structure de base de l’élément Table</span><span class="sxs-lookup"><span data-stu-id="92206-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
-   [<span data-ttu-id="92206-109">Imbrication des tables</span><span class="sxs-lookup"><span data-stu-id="92206-109">Table Containment</span></span>](#table_containment)  
  
-   [<span data-ttu-id="92206-110">Regroupements de lignes</span><span class="sxs-lookup"><span data-stu-id="92206-110">Row Groupings</span></span>](#row_groupings)  
  
-   [<span data-ttu-id="92206-111">Priorité du rendu en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="92206-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
-   [<span data-ttu-id="92206-112">Étendue des lignes et des colonnes</span><span class="sxs-lookup"><span data-stu-id="92206-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
-   [<span data-ttu-id="92206-113">Génération d’une table avec du code</span><span class="sxs-lookup"><span data-stu-id="92206-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
-   <span data-ttu-id="92206-114">[Rubriques connexes]</span><span class="sxs-lookup"><span data-stu-id="92206-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="92206-115">Principes de base de l’élément Table</span><span class="sxs-lookup"><span data-stu-id="92206-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="92206-116">Différences entre l’élément Table et l’élément Grid</span><span class="sxs-lookup"><span data-stu-id="92206-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="92206-117"><xref:System.Windows.Documents.Table>et <xref:System.Windows.Controls.Grid> partagent des fonctionnalités communes, mais chacun est parfaitement adapté pour différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="92206-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="92206-118">A <xref:System.Windows.Documents.Table> est conçu pour une utilisation dans le contenu de flux (consultez [vue d’ensemble du Document de flux](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pour plus d’informations sur le contenu de flux).</span><span class="sxs-lookup"><span data-stu-id="92206-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="92206-119">Les éléments Grid sont mieux adaptés à une utilisation dans des formulaires (autrement dit, partout, sauf dans du contenu dynamique).</span><span class="sxs-lookup"><span data-stu-id="92206-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="92206-120">Dans un <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> prend en charge comportements de contenu tels que la pagination et sélection de contenu lors de la redistribution de la colonne un <xref:System.Windows.Controls.Grid> n’est pas.</span><span class="sxs-lookup"><span data-stu-id="92206-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="92206-121">A <xref:System.Windows.Controls.Grid> quant à eux permet à l’extérieur d’un <xref:System.Windows.Documents.FlowDocument> pour de nombreuses raisons, y compris <xref:System.Windows.Controls.Grid> ajoute des éléments basés sur un index de ligne et de colonne, <xref:System.Windows.Documents.Table> n’est pas.</span><span class="sxs-lookup"><span data-stu-id="92206-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="92206-122">Le <xref:System.Windows.Controls.Grid> élément autorise la superposition du contenu enfant, ce qui permet de plusieurs éléments d’exister dans un seul « cellule ».</span><span class="sxs-lookup"><span data-stu-id="92206-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="92206-123"><xref:System.Windows.Documents.Table>ne prend pas en charge la superposition.</span><span class="sxs-lookup"><span data-stu-id="92206-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="92206-124">Éléments enfants d’un <xref:System.Windows.Controls.Grid> peut être positionné par rapport à la zone de leurs limites de « cellule ».</span><span class="sxs-lookup"><span data-stu-id="92206-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="92206-125"><xref:System.Windows.Documents.Table>ne prend pas en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="92206-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="92206-126">Enfin, un <xref:System.Windows.Controls.Grid> requiert moins de ressources un <xref:System.Windows.Documents.Table> , envisagez d’utiliser un <xref:System.Windows.Controls.Grid> pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="92206-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="92206-127">Structure de base de l’élément Table</span><span class="sxs-lookup"><span data-stu-id="92206-127">Basic Table Structure</span></span>  
 <span data-ttu-id="92206-128"><xref:System.Windows.Documents.Table>Fournit une présentation grille composée de colonnes (représentées par <xref:System.Windows.Documents.TableColumn> éléments) et des lignes (représentés par <xref:System.Windows.Documents.TableRow> éléments).</span><span class="sxs-lookup"><span data-stu-id="92206-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="92206-129"><xref:System.Windows.Documents.TableColumn>éléments n’hébergent pas de contenu ; ils définissent simplement les colonnes et les caractéristiques des colonnes.</span><span class="sxs-lookup"><span data-stu-id="92206-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="92206-130"><xref:System.Windows.Documents.TableRow>les éléments doivent être hébergés dans un <xref:System.Windows.Documents.TableRowGroup> élément, qui définit un regroupement de lignes pour la table.</span><span class="sxs-lookup"><span data-stu-id="92206-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="92206-131"><xref:System.Windows.Documents.TableCell>éléments qui contiennent le contenu réel à être présentés par la table, doivent être hébergés dans un <xref:System.Windows.Documents.TableRow> élément.</span><span class="sxs-lookup"><span data-stu-id="92206-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="92206-132"><xref:System.Windows.Documents.TableCell>peut uniquement contenir des éléments qui dérivent de <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="92206-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="92206-133">Éléments enfants valides pour un <xref:System.Windows.Documents.TableCell> inclure.</span><span class="sxs-lookup"><span data-stu-id="92206-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="92206-134"><xref:System.Windows.Documents.TableCell>les éléments ne peuvent pas héberger directement le contenu de texte.</span><span class="sxs-lookup"><span data-stu-id="92206-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="92206-135">Pour plus d’informations sur les règles de relation contenant-contenu de flux comme les éléments de contenu <xref:System.Windows.Documents.TableCell>, consultez [vue d’ensemble du Document de flux](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="92206-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92206-136"><xref:System.Windows.Documents.Table>est similaire à la <xref:System.Windows.Controls.Grid> élément mais n’a plus de capacités et, par conséquent, requiert une charge importante de ressources.</span><span class="sxs-lookup"><span data-stu-id="92206-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="92206-137">L’exemple suivant définit une table 2 x 3 simple avec [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92206-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="92206-138">La figure suivante montre le rendu de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="92206-138">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="92206-139">![Capture d’écran : affichage d’une table de base](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span><span class="sxs-lookup"><span data-stu-id="92206-139">![Screenshot: Render a basic table](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span></span>  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="92206-140">Imbrication des tables</span><span class="sxs-lookup"><span data-stu-id="92206-140">Table Containment</span></span>  
 <span data-ttu-id="92206-141"><xref:System.Windows.Documents.Table>dérive de la <xref:System.Windows.Documents.Block> élément et sont conformes aux règles communes pour <xref:System.Windows.Documents.Block> éléments de niveau.</span><span class="sxs-lookup"><span data-stu-id="92206-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="92206-142">A <xref:System.Windows.Documents.Table> élément peut être contenu dans un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="92206-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="92206-143">Regroupements de lignes</span><span class="sxs-lookup"><span data-stu-id="92206-143">Row Groupings</span></span>  
 <span data-ttu-id="92206-144">Le <xref:System.Windows.Documents.TableRowGroup> élément permet de grouper arbitrairement des lignes dans une table ; chaque ligne dans une table doit appartenir à un regroupement de lignes.</span><span class="sxs-lookup"><span data-stu-id="92206-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="92206-145">Les lignes qui sont regroupées ont souvent un but commun et il est donc possible d’appliquer un style à l’ensemble du regroupement.</span><span class="sxs-lookup"><span data-stu-id="92206-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="92206-146">Il est courant, pour les regroupements de lignes, de séparer les lignes spéciales, telles que les titres, les en-têtes et les pieds de page, du contenu principal de la table.</span><span class="sxs-lookup"><span data-stu-id="92206-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="92206-147">L’exemple suivant utilise [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pour définir une table avec des lignes d’en-tête et pied de page appliqués.</span><span class="sxs-lookup"><span data-stu-id="92206-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="92206-148">La figure suivante montre le rendu de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="92206-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="92206-149">![Capture d’écran : groupes de lignes de la table](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="92206-149">![Screenshot: Table row groups](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="92206-150">Priorité du rendu en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="92206-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="92206-151">Les éléments de la table sont affichés dans l’ordre suivant (dans l’ordre de plan, du plus bas au plus haut).</span><span class="sxs-lookup"><span data-stu-id="92206-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="92206-152">Cet ordre ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="92206-152">This order cannot be changed.</span></span> <span data-ttu-id="92206-153">Par exemple, il n’existe pas de propriété « Ordre de plan » que vous pourriez utiliser pour remplacer l’ordre établi.</span><span class="sxs-lookup"><span data-stu-id="92206-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="92206-154">Prenons l’exemple suivant, qui définit des couleurs d’arrière-plan dans une table pour chacun de ces éléments.</span><span class="sxs-lookup"><span data-stu-id="92206-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="92206-155">La figure suivante montre comment s’affiche cet exemple (seules les couleurs d’arrière-plan sont affichées).</span><span class="sxs-lookup"><span data-stu-id="92206-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="92206-156">![Capture d’écran : ordre de plan de la table](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="92206-156">![Screenshot: Table z&#45;order](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="92206-157">Étendue des lignes et des colonnes</span><span class="sxs-lookup"><span data-stu-id="92206-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="92206-158">Les cellules de tableau peuvent être configurées pour s’étendre sur plusieurs lignes ou colonnes à l’aide de la <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> des attributs, respectivement.</span><span class="sxs-lookup"><span data-stu-id="92206-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="92206-159">Prenons l’exemple suivant, dans lequel une cellule s’étend sur trois colonnes.</span><span class="sxs-lookup"><span data-stu-id="92206-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="92206-160">La figure suivante montre le rendu de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="92206-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="92206-161">![Capture d’écran : cellule s’étendant sur les trois colonnes](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="92206-161">![Screenshot: Cell spanning all three columns](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="92206-162">Génération d’une table avec du code</span><span class="sxs-lookup"><span data-stu-id="92206-162">Building a Table With Code</span></span>  
 <span data-ttu-id="92206-163">Les exemples suivants montrent comment créer par programmation un <xref:System.Windows.Documents.Table> et le remplir avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="92206-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="92206-164">Le contenu de la table est réparti en cinq lignes (représentés par <xref:System.Windows.Documents.TableRow> objets contenus dans un <xref:System.Windows.Documents.Table.RowGroups%2A> objet) et six colonnes (représentées par <xref:System.Windows.Documents.TableColumn> objets).</span><span class="sxs-lookup"><span data-stu-id="92206-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="92206-165">Les lignes sont utilisées pour différentes présentations, par exemple une ligne de titre prévue pour intituler l’ensemble de la table, une ligne d’en-tête pour décrire les colonnes de données d’une table ou une ligne de pied de page avec des informations de synthèse.</span><span class="sxs-lookup"><span data-stu-id="92206-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="92206-166">Notez que les lignes de titre, d’en-tête et de pied de page ne sont pas inhérentes à la table. Il s’agit simplement de lignes présentant des caractéristiques différentes.</span><span class="sxs-lookup"><span data-stu-id="92206-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="92206-167">Cellules de tableau contiennent le contenu réel, qui peut être composé de texte, des images ou presque n’importe quel autre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] élément.</span><span class="sxs-lookup"><span data-stu-id="92206-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="92206-168">Tout d’abord, un <xref:System.Windows.Documents.FlowDocument> est créée pour héberger le <xref:System.Windows.Documents.Table>et une nouvelle <xref:System.Windows.Documents.Table> est créé et ajouté au contenu de la <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="92206-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="92206-169">Ensuite, six <xref:System.Windows.Documents.TableColumn> objets sont créés et ajoutés à la table <xref:System.Windows.Documents.Table.Columns%2A> collection avec une mise en forme appliquée.</span><span class="sxs-lookup"><span data-stu-id="92206-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92206-170">Notez que la table <xref:System.Windows.Documents.Table.Columns%2A> collection utilise l’indexation standard de base zéro.</span><span class="sxs-lookup"><span data-stu-id="92206-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="92206-171">Ensuite, une ligne de titre est créée, puis ajoutée à la table avec une mise en forme.</span><span class="sxs-lookup"><span data-stu-id="92206-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="92206-172">La ligne de titre contient une seule cellule qui s’étend sur les six colonnes de la table.</span><span class="sxs-lookup"><span data-stu-id="92206-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="92206-173">Ensuite, une ligne d’en-tête est créée, puis ajoutée à la table, et les cellules de la ligne d’en-tête sont créées, puis remplies avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="92206-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="92206-174">Ensuite, une ligne de données est créée, puis ajoutée à la table, et les cellules de cette ligne sont créées, puis remplies avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="92206-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="92206-175">La génération de cette ligne est similaire à la création de la ligne d’en-tête. Cependant, la mise en forme appliquée est légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="92206-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="92206-176">Enfin, une ligne de pied de page est créée, ajoutée, puis mise en forme.</span><span class="sxs-lookup"><span data-stu-id="92206-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="92206-177">Tout comme la ligne de titre, le pied de page contient une seule cellule qui s’étend sur les six colonnes de la table.</span><span class="sxs-lookup"><span data-stu-id="92206-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="92206-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92206-178">See Also</span></span>  
 [<span data-ttu-id="92206-179">Vue d’ensemble des documents dynamiques</span><span class="sxs-lookup"><span data-stu-id="92206-179">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="92206-180">Définir une table avec XAML</span><span class="sxs-lookup"><span data-stu-id="92206-180">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="92206-181">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="92206-181">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="92206-182">Utiliser les éléments de contenu de flux</span><span class="sxs-lookup"><span data-stu-id="92206-182">Use Flow Content Elements</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
