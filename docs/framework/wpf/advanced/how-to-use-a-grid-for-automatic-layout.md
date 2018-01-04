---
title: Guide pratique pour utiliser une grille pour la disposition automatique
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbd8bd7e36b7b773837b839e77ec88a8e7c8f0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="c8fdb-102">Guide pratique pour utiliser une grille pour la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="c8fdb-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="c8fdb-103">Cet exemple décrit comment utiliser une grille quand vous tirez parti de la disposition automatique pour créer une application localisable.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="c8fdb-104">Localisation d’un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="c8fdb-105">Les localisateurs doivent souvent redimensionner et repositionner les éléments, en plus de traduire le texte.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="c8fdb-106">Dans le passé chaque langue qu’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a été adaptée pour l’ajustement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="c8fdb-107">Désormais, avec les fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous pouvez concevoir des éléments qui réduisent les ajustements nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="c8fdb-108">L’approche consistant à écrire des applications qui peuvent être plus facilement redimensionné et repositionné est appelée `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="c8fdb-109">Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemple illustre l’utilisation d’une grille pour positionner des boutons et du texte.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="c8fdb-110">Notez que la hauteur et la largeur des cellules sont définies pour `Auto`; par conséquent, la cellule qui contient le bouton avec une image s’ajuste à l’image.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="c8fdb-111">Étant donné que le <xref:System.Windows.Controls.Grid> élément peut ajuster à son contenu, il peut être utile lorsque vous effectuez l’approche de mise en page automatique pour concevoir des applications qui peuvent être localisées.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8fdb-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8fdb-112">Example</span></span>  
 <span data-ttu-id="c8fdb-113">L’exemple suivant montre comment utiliser une grille.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="c8fdb-114">Le graphique suivant montre la sortie générée par l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="c8fdb-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="c8fdb-115">![Exemple de grille](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="c8fdb-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="c8fdb-116">Grille</span><span class="sxs-lookup"><span data-stu-id="c8fdb-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fdb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8fdb-117">See Also</span></span>  
 [<span data-ttu-id="c8fdb-118">Vue d’ensemble de l’utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="c8fdb-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="c8fdb-119">Utiliser la disposition automatique pour créer un bouton</span><span class="sxs-lookup"><span data-stu-id="c8fdb-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
