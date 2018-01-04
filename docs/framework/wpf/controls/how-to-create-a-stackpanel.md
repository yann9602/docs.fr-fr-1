---
title: "Comment : créer un StackPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9226ac10e4f221cc381b7c59179b2667e20aa757
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="2b33c-102">Comment : créer un StackPanel</span><span class="sxs-lookup"><span data-stu-id="2b33c-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="2b33c-103">Cet exemple montre comment créer un <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2b33c-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b33c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b33c-104">Example</span></span>  
 <span data-ttu-id="2b33c-105">A <xref:System.Windows.Controls.StackPanel> vous permet d’empiler des éléments dans une direction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2b33c-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="2b33c-106">À l’aide des propriétés qui sont définies sur <xref:System.Windows.Controls.StackPanel>, le contenu peut circuler verticalement, qui est le paramètre par défaut, ou horizontalement.</span><span class="sxs-lookup"><span data-stu-id="2b33c-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="2b33c-107">L’exemple suivant empile verticalement cinq <xref:System.Windows.Controls.TextBlock> des contrôles, chacun avec un autre <xref:System.Windows.Controls.Border> et <xref:System.Windows.Controls.Border.Background%2A>, à l’aide de <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2b33c-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="2b33c-108">Les éléments enfants qui n’ont pas spécifié <xref:System.Windows.FrameworkElement.Width%2A> s’étire pour remplir la fenêtre parente ; Toutefois, les éléments enfants qui ont un <xref:System.Windows.FrameworkElement.Width%2A>, est centré dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="2b33c-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="2b33c-109">La direction de la pile par défaut dans un <xref:System.Windows.Controls.StackPanel> est vertical.</span><span class="sxs-lookup"><span data-stu-id="2b33c-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="2b33c-110">Pour les flux de contrôle contenu dans un <xref:System.Windows.Controls.StackPanel>, utilisez le <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2b33c-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="2b33c-111">Vous pouvez contrôler l’alignement horizontal en utilisant la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2b33c-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b33c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b33c-112">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="2b33c-113">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="2b33c-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="2b33c-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2b33c-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
