---
title: "Comment : créer un mode d'affichage personnalisé pour un ListView"
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
helpviewer_keywords: ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c62bcb14f444490991b36dc21eb7676a67007906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Comment : créer un mode d'affichage personnalisé pour un ListView
Cet exemple montre comment créer un personnalisé <xref:System.Windows.Controls.ListView.View%2A> mode pour un <xref:System.Windows.Controls.ListView> contrôle.  
  
## <a name="example"></a>Exemple  
 Vous devez utiliser le <xref:System.Windows.Controls.ViewBase> classe lorsque vous créez un affichage personnalisé pour le <xref:System.Windows.Controls.ListView> contrôle. L’exemple suivant montre un mode d’affichage appelé `PlainView`, qui est dérivée de la <xref:System.Windows.Controls.ViewBase> classe.  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Pour appliquer un style à la vue personnalisée, utilisez la <xref:System.Windows.Style> classe. L’exemple suivant définit un <xref:System.Windows.Style> pour la `PlainView` mode d’affichage. Dans l’exemple précédent, ce style est défini en tant que la valeur de la <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> propriété qui est définie pour `PlainView`.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Pour définir la disposition des données dans un mode d’affichage personnalisé, définissez un <xref:System.Windows.DataTemplate> objet. L’exemple suivant définit un <xref:System.Windows.DataTemplate> qui peut être utilisé pour afficher des données dans la `PlainView` mode d’affichage.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.ResourceKey> pour le `PlainView` mode d’affichage qui utilise le <xref:System.Windows.DataTemplate> qui est définie dans l’exemple précédent.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A <xref:System.Windows.Controls.ListView> contrôle peut utiliser une vue personnalisée si vous définissez le <xref:System.Windows.Controls.ListView.View%2A> propriété à la clé de ressource. L’exemple suivant montre comment spécifier `PlainView` comme mode d’affichage pour un <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Pour obtenir un exemple complet, consultez [ListView avec plusieurs vues, exemple](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Vue d’ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
