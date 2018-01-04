---
title: "Comment : utiliser des modèles pour appliquer un style à un ListView utilisant GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9abc19ca14cf512deff898f5f20d23870b8b7847
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="f75f6-102">Comment : utiliser des modèles pour appliquer un style à un ListView utilisant GridView</span><span class="sxs-lookup"><span data-stu-id="f75f6-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="f75f6-103">Cet exemple montre comment utiliser le <xref:System.Windows.DataTemplate> et <xref:System.Windows.Style> objets pour spécifier l’apparence d’un <xref:System.Windows.Controls.ListView> contrôle qui utilise un <xref:System.Windows.Controls.GridView> mode d’affichage.</span><span class="sxs-lookup"><span data-stu-id="f75f6-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f75f6-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f75f6-104">Example</span></span>  
 <span data-ttu-id="f75f6-105">Les exemples suivants montrent <xref:System.Windows.Style> et <xref:System.Windows.DataTemplate> objets permettant de personnaliser l’apparence d’un en-tête de colonne pour un <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="f75f6-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="f75f6-106">L’exemple suivant montre comment utiliser ces <xref:System.Windows.Style> et <xref:System.Windows.DataTemplate> objets pour définir le <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> et <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> propriétés d’un <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="f75f6-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="f75f6-107">Le <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété définit le contenu des cellules de la colonne.</span><span class="sxs-lookup"><span data-stu-id="f75f6-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="f75f6-108">Le <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> et <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> ne sont que deux de plusieurs propriétés que vous pouvez utiliser pour personnaliser l’apparence d’en-tête de colonne pour un <xref:System.Windows.Controls.GridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f75f6-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="f75f6-109">Pour plus d’informations, consultez [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f75f6-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="f75f6-110">L’exemple suivant montre comment définir un <xref:System.Windows.DataTemplate> qui personnalise l’apparence des cellules dans un <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="f75f6-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="f75f6-111">L’exemple suivant montre comment utiliser ce <xref:System.Windows.DataTemplate> pour définir le contenu d’un <xref:System.Windows.Controls.GridViewColumn> cellule.</span><span class="sxs-lookup"><span data-stu-id="f75f6-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="f75f6-112">Ce modèle est utilisé à la place de la <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété qui est indiquée dans le précédent <xref:System.Windows.Controls.GridViewColumn> exemple.</span><span class="sxs-lookup"><span data-stu-id="f75f6-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="f75f6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f75f6-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="f75f6-114">Vue d’ensemble de GridView</span><span class="sxs-lookup"><span data-stu-id="f75f6-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="f75f6-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="f75f6-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="f75f6-116">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="f75f6-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
