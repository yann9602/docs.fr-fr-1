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
ms.workload: dotnet
ms.openlocfilehash: e67777b5568214dff889088708db166efc6ae4dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="6cc62-102">Comment : créer un mode d'affichage personnalisé pour un ListView</span><span class="sxs-lookup"><span data-stu-id="6cc62-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="6cc62-103">Cet exemple montre comment créer un personnalisé <xref:System.Windows.Controls.ListView.View%2A> mode pour un <xref:System.Windows.Controls.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6cc62-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cc62-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="6cc62-104">Example</span></span>  
 <span data-ttu-id="6cc62-105">Vous devez utiliser le <xref:System.Windows.Controls.ViewBase> classe lorsque vous créez un affichage personnalisé pour le <xref:System.Windows.Controls.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6cc62-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="6cc62-106">L’exemple suivant montre un mode d’affichage appelé `PlainView`, qui est dérivée de la <xref:System.Windows.Controls.ViewBase> classe.</span><span class="sxs-lookup"><span data-stu-id="6cc62-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="6cc62-107">Pour appliquer un style à la vue personnalisée, utilisez la <xref:System.Windows.Style> classe.</span><span class="sxs-lookup"><span data-stu-id="6cc62-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="6cc62-108">L’exemple suivant définit un <xref:System.Windows.Style> pour la `PlainView` mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="6cc62-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="6cc62-109">Dans l’exemple précédent, ce style est défini en tant que la valeur de la <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> propriété qui est définie pour `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="6cc62-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="6cc62-110">Pour définir la disposition des données dans un mode d’affichage personnalisé, définissez un <xref:System.Windows.DataTemplate> objet.</span><span class="sxs-lookup"><span data-stu-id="6cc62-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="6cc62-111">L’exemple suivant définit un <xref:System.Windows.DataTemplate> qui peut être utilisé pour afficher des données dans la `PlainView` mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="6cc62-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="6cc62-112">L’exemple suivant montre comment définir un <xref:System.Windows.ResourceKey> pour le `PlainView` mode d’affichage qui utilise le <xref:System.Windows.DataTemplate> qui est définie dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="6cc62-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="6cc62-113">A <xref:System.Windows.Controls.ListView> contrôle peut utiliser une vue personnalisée si vous définissez le <xref:System.Windows.Controls.ListView.View%2A> propriété à la clé de ressource.</span><span class="sxs-lookup"><span data-stu-id="6cc62-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="6cc62-114">L’exemple suivant montre comment spécifier `PlainView` comme mode d’affichage pour un <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="6cc62-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="6cc62-115">Pour obtenir un exemple complet, consultez [ListView avec plusieurs vues, exemple](http://go.microsoft.com/fwlink/?LinkID=160013).</span><span class="sxs-lookup"><span data-stu-id="6cc62-115">For the complete sample, see [ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc62-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cc62-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="6cc62-117">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="6cc62-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="6cc62-118">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="6cc62-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="6cc62-119">Vue d’ensemble de GridView</span><span class="sxs-lookup"><span data-stu-id="6cc62-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
