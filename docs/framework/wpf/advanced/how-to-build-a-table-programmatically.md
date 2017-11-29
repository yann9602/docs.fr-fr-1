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
ms.openlocfilehash: 8ef961bb219f201cf5fe32a5b2bbdf70ef45e73b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a>Comment : générer une table par programmation
Les exemples suivants montrent comment créer par programmation un <xref:System.Windows.Documents.Table> et le remplir avec le contenu. Le contenu de la table est réparti en cinq lignes (représentés par <xref:System.Windows.Documents.TableRow> objets contenus dans un <xref:System.Windows.Documents.Table.RowGroups%2A> objet) et six colonnes (représentées par <xref:System.Windows.Documents.TableColumn> objets). Les lignes sont utilisées pour différentes présentations, par exemple une ligne de titre prévue pour intituler l’ensemble de la table, une ligne d’en-tête pour décrire les colonnes de données d’une table ou une ligne de pied de page avec des informations de synthèse.  Notez que les lignes de titre, d’en-tête et de pied de page ne sont pas inhérentes à la table. Il s’agit simplement de lignes présentant des caractéristiques différentes. Cellules de tableau contiennent le contenu réel, qui peut être composé de texte, des images ou presque n’importe quel autre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] élément.  
  
## <a name="example"></a>Exemple  
 Tout d’abord, un <xref:System.Windows.Documents.FlowDocument> est créée pour héberger le <xref:System.Windows.Documents.Table>et une nouvelle <xref:System.Windows.Documents.Table> est créé et ajouté au contenu de la <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Exemple  
 Ensuite, six <xref:System.Windows.Documents.TableColumn> objets sont créés et ajoutés à la table <xref:System.Windows.Documents.Table.Columns%2A> collection avec une mise en forme appliquée.  
  
> [!NOTE]
>  Notez que la table <xref:System.Windows.Documents.Table.Columns%2A> collection utilise l’indexation standard de base zéro.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Exemple  
 Ensuite, une ligne de titre est créée, puis ajoutée à la table avec une mise en forme.  La ligne de titre contient une seule cellule qui s’étend sur les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Exemple  
 Ensuite, une ligne d’en-tête est créée, puis ajoutée à la table, et les cellules de la ligne d’en-tête sont créées, puis remplies avec le contenu.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Exemple  
 Ensuite, une ligne de données est créée, puis ajoutée à la table, et les cellules de cette ligne sont créées, puis remplies avec le contenu.  La génération de cette ligne est similaire à la création de la ligne d’en-tête. Cependant, la mise en forme appliquée est légèrement différente.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Exemple  
 Enfin, une ligne de pied de page est créée, ajoutée, puis mise en forme.  Tout comme la ligne de titre, le pied de page contient une seule cellule qui s’étend sur les six colonnes de la table.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)
