---
title: "Comment : définir une table avec XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b932c7df822edabc5626f20af2bfc1eb3a7f93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="76084-102">Comment : définir une table avec XAML</span><span class="sxs-lookup"><span data-stu-id="76084-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="76084-103">L’exemple suivant montre comment définir un <xref:System.Windows.Documents.Table> à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76084-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="76084-104">L’exemple de tableau a quatre colonnes (représentées par <xref:System.Windows.Documents.TableColumn> éléments) et plusieurs lignes (représenté par <xref:System.Windows.Documents.TableRow> éléments) contenant des données ainsi que le titre, en-tête et les informations de pied de page.</span><span class="sxs-lookup"><span data-stu-id="76084-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="76084-105">Lignes doivent être contenues dans un <xref:System.Windows.Documents.TableRowGroup> élément.</span><span class="sxs-lookup"><span data-stu-id="76084-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="76084-106">Chaque ligne dans la table est composée d’une ou plusieurs cellules (représentées par <xref:System.Windows.Documents.TableCell> éléments).</span><span class="sxs-lookup"><span data-stu-id="76084-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="76084-107">Le contenu dans une cellule de tableau doit être contenu dans un <xref:System.Windows.Documents.Block> élément ; dans ce cas <xref:System.Windows.Documents.Paragraph> les éléments sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="76084-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="76084-108">Le tableau héberge également un lien hypertexte (représenté par la <xref:System.Windows.Documents.Hyperlink> élément) dans la ligne de pied de page.</span><span class="sxs-lookup"><span data-stu-id="76084-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76084-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="76084-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="76084-110">La figure suivante illustre le rendu de la table définie dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="76084-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="76084-111">![Table affichée.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="76084-111">![Rendered table.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span></span>
