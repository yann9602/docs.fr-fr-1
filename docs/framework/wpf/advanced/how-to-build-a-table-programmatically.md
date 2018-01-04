---
title: "Comment : générer une table par programmation"
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
helpviewer_keywords: tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca6a304ea12dd90a71f8718fed5f1595f4cd4b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="1c865-102">Comment : générer une table par programmation</span><span class="sxs-lookup"><span data-stu-id="1c865-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="1c865-103">Les exemples suivants montrent comment créer par programmation un <xref:System.Windows.Documents.Table> et le remplir avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="1c865-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="1c865-104">Le contenu de la table est réparti en cinq lignes (représentés par <xref:System.Windows.Documents.TableRow> objets contenus dans un <xref:System.Windows.Documents.Table.RowGroups%2A> objet) et six colonnes (représentées par <xref:System.Windows.Documents.TableColumn> objets).</span><span class="sxs-lookup"><span data-stu-id="1c865-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="1c865-105">Les lignes sont utilisées pour différentes présentations, par exemple une ligne de titre prévue pour intituler l’ensemble de la table, une ligne d’en-tête pour décrire les colonnes de données d’une table ou une ligne de pied de page avec des informations de synthèse.</span><span class="sxs-lookup"><span data-stu-id="1c865-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="1c865-106">Notez que les lignes de titre, d’en-tête et de pied de page ne sont pas inhérentes à la table. Il s’agit simplement de lignes présentant des caractéristiques différentes.</span><span class="sxs-lookup"><span data-stu-id="1c865-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="1c865-107">Cellules de tableau contiennent le contenu réel, qui peut être composé de texte, des images ou presque n’importe quel autre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] élément.</span><span class="sxs-lookup"><span data-stu-id="1c865-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c865-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c865-108">Example</span></span>  
 <span data-ttu-id="1c865-109">Tout d’abord, un <xref:System.Windows.Documents.FlowDocument> est créée pour héberger le <xref:System.Windows.Documents.Table>et une nouvelle <xref:System.Windows.Documents.Table> est créé et ajouté au contenu de la <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="1c865-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="1c865-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c865-110">Example</span></span>  
 <span data-ttu-id="1c865-111">Ensuite, six <xref:System.Windows.Documents.TableColumn> objets sont créés et ajoutés à la table <xref:System.Windows.Documents.Table.Columns%2A> collection avec une mise en forme appliquée.</span><span class="sxs-lookup"><span data-stu-id="1c865-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c865-112">Notez que la table <xref:System.Windows.Documents.Table.Columns%2A> collection utilise l’indexation standard de base zéro.</span><span class="sxs-lookup"><span data-stu-id="1c865-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="1c865-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c865-113">Example</span></span>  
 <span data-ttu-id="1c865-114">Ensuite, une ligne de titre est créée, puis ajoutée à la table avec une mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1c865-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="1c865-115">La ligne de titre contient une seule cellule qui s’étend sur les six colonnes de la table.</span><span class="sxs-lookup"><span data-stu-id="1c865-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="1c865-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c865-116">Example</span></span>  
 <span data-ttu-id="1c865-117">Ensuite, une ligne d’en-tête est créée, puis ajoutée à la table, et les cellules de la ligne d’en-tête sont créées, puis remplies avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="1c865-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="1c865-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c865-118">Example</span></span>  
 <span data-ttu-id="1c865-119">Ensuite, une ligne de données est créée, puis ajoutée à la table, et les cellules de cette ligne sont créées, puis remplies avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="1c865-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="1c865-120">La génération de cette ligne est similaire à la création de la ligne d’en-tête. Cependant, la mise en forme appliquée est légèrement différente.</span><span class="sxs-lookup"><span data-stu-id="1c865-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="1c865-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c865-121">Example</span></span>  
 <span data-ttu-id="1c865-122">Enfin, une ligne de pied de page est créée, ajoutée, puis mise en forme.</span><span class="sxs-lookup"><span data-stu-id="1c865-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="1c865-123">Tout comme la ligne de titre, le pied de page contient une seule cellule qui s’étend sur les six colonnes de la table.</span><span class="sxs-lookup"><span data-stu-id="1c865-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="1c865-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c865-124">See Also</span></span>  
 [<span data-ttu-id="1c865-125">Vue d’ensemble de Table</span><span class="sxs-lookup"><span data-stu-id="1c865-125">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
