---
title: "Vue d'ensemble des modèles et styles d'en-tête de colonne GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad0f7cacc8256e060bb12611bd1818b694e1e6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="886fe-102">Vue d'ensemble des modèles et styles d'en-tête de colonne GridView</span><span class="sxs-lookup"><span data-stu-id="886fe-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="886fe-103">Cette présentation décrit l’ordre de priorité pour les propriétés qui vous permet de personnaliser un en-tête de colonne dans la <xref:System.Windows.Controls.GridView> mode d’affichage d’un <xref:System.Windows.Controls.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="886fe-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="886fe-104">Personnalisation d’un en-tête de colonne dans un GridView</span><span class="sxs-lookup"><span data-stu-id="886fe-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="886fe-105">Les propriétés qui définissent le contenu, la disposition et le style d’un en-tête de colonne dans un <xref:System.Windows.Controls.GridView> se trouvent dans de nombreuses classes connexes.</span><span class="sxs-lookup"><span data-stu-id="886fe-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="886fe-106">Certaines de ces propriétés ont des fonctionnalités similaires ou identiques.</span><span class="sxs-lookup"><span data-stu-id="886fe-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="886fe-107">Les lignes dans le tableau suivant affichent les groupes de propriétés qui exécutent la même fonction.</span><span class="sxs-lookup"><span data-stu-id="886fe-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="886fe-108">Vous pouvez utiliser ces propriétés pour personnaliser les en-têtes de colonne dans un <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="886fe-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="886fe-109">L’ordre de priorité des propriétés connexes est de droite à gauche où la propriété dans la colonne de droite plus lointain a la priorité la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="886fe-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="886fe-110">Par exemple, si un <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> est définie sur le <xref:System.Windows.Controls.GridViewColumnHeader> objet et la <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> est défini sur associé <xref:System.Windows.Controls.GridViewColumn>, le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="886fe-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="886fe-111">Dans ce scénario, le <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="886fe-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="886fe-112">**Propriétés connexes pour les en-têtes de colonne dans un GridView**</span><span class="sxs-lookup"><span data-stu-id="886fe-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="886fe-113">**Classes**</span><span class="sxs-lookup"><span data-stu-id="886fe-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="886fe-114">**Propriétés du Menu contextuel**</span><span class="sxs-lookup"><span data-stu-id="886fe-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="886fe-115">Non applicable</span><span class="sxs-lookup"><span data-stu-id="886fe-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="886fe-116">**ToolTip**</span><span class="sxs-lookup"><span data-stu-id="886fe-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="886fe-117">**Propriétés**</span><span class="sxs-lookup"><span data-stu-id="886fe-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="886fe-118">Non applicable</span><span class="sxs-lookup"><span data-stu-id="886fe-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="886fe-119">**Modèle d’en-tête**</span><span class="sxs-lookup"><span data-stu-id="886fe-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="886fe-120">**Propriétés**</span><span class="sxs-lookup"><span data-stu-id="886fe-120">**Properties**</span></span>|<span data-ttu-id="886fe-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="886fe-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="886fe-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="886fe-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="886fe-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="886fe-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="886fe-124">**Propriétés de style**</span><span class="sxs-lookup"><span data-stu-id="886fe-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="886fe-125"><sup>1</sup>pour **propriétés de modèle d’en-tête**, si vous définissez les propriétés du sélecteur de modèle et le modèle, la propriété de modèle est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="886fe-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="886fe-126">Par exemple, si vous définissez à la fois le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> propriétés, le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="886fe-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886fe-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="886fe-127">See Also</span></span>  
 [<span data-ttu-id="886fe-128">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="886fe-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="886fe-129">Vue d’ensemble de ListView</span><span class="sxs-lookup"><span data-stu-id="886fe-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="886fe-130">Vue d’ensemble de GridView</span><span class="sxs-lookup"><span data-stu-id="886fe-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
