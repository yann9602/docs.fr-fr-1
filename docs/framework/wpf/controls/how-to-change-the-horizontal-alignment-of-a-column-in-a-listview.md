---
title: "Comment : modifier l'alignement horizontal d'une colonne dans un ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a465ae44d3b8a4c43e5e34eaeedcd739d328bff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Comment : modifier l'alignement horizontal d'une colonne dans un ListView
Par défaut, le contenu de chaque colonne dans un <xref:System.Windows.Controls.ListViewItem> est aligné à gauche. Vous pouvez modifier l’alignement de chaque colonne en fournissant un <xref:System.Windows.DataTemplate> et en définissant le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété sur l’élément dans le <xref:System.Windows.DataTemplate>. Cette rubrique montre comment un <xref:System.Windows.Controls.ListView> aligne son contenu par défaut et comment modifier l’alignement d’une colonne dans un <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les données dans le `Title` et `ISBN` de colonnes est aligné à gauche.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Pour modifier l’alignement de la `ISBN` colonne, vous devez spécifier que le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> propriété de chaque <xref:System.Windows.Controls.ListViewItem> est <xref:System.Windows.HorizontalAlignment.Stretch>, de sorte que les éléments de chaque <xref:System.Windows.Controls.ListViewItem> peut couvrir ou être positionnés sur toute la largeur de chaque colonne. Étant donné que la <xref:System.Windows.Controls.ListView> est lié à une source de données, vous devez créer un style qui définit le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Ensuite, vous devez utiliser un <xref:System.Windows.DataTemplate> pour afficher le contenu au lieu d’utiliser le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété. Pour afficher le `ISBN` de chaque modèle, le <xref:System.Windows.DataTemplate> peut uniquement contenir une <xref:System.Windows.Controls.TextBlock> qui a son <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Right>.  
  
 L’exemple suivant définit le style et <xref:System.Windows.DataTemplate> nécessaire pour effectuer la `ISBN` colonne aligné à droite et les modifications le <xref:System.Windows.Controls.GridViewColumn> référence le <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vue d’ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)
