---
title: "Comment : partager des propriétés de dimensionnement entre grilles"
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
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8f80d93f9625ff962a3e3fab1f6647678ecf32f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="de2f4-102">Comment : partager des propriétés de dimensionnement entre grilles</span><span class="sxs-lookup"><span data-stu-id="de2f4-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="de2f4-103">Cet exemple montre comment partager les données de dimensionnement des colonnes et des lignes entre <xref:System.Windows.Controls.Grid> éléments afin de conserver une taille cohérente.</span><span class="sxs-lookup"><span data-stu-id="de2f4-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de2f4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="de2f4-104">Example</span></span>  
 <span data-ttu-id="de2f4-105">L’exemple suivant présente deux <xref:System.Windows.Controls.Grid> éléments en tant qu’éléments enfants d’un parent <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="de2f4-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="de2f4-106">Le <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> propriété de jointe <xref:System.Windows.Controls.Grid> est défini sur le parent <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="de2f4-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="de2f4-107">L’exemple manipule la valeur de propriété à l’aide de deux <xref:System.Windows.Controls.Button> éléments ; chaque élément représente une des valeurs de propriété booléenne.</span><span class="sxs-lookup"><span data-stu-id="de2f4-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="de2f4-108">Lorsque le <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> propriété a la valeur `true`, chaque membre de colonne ou ligne d’un <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> partage des informations sur le dimensionnement, quel que soit le contenu d’une ligne ou colonne.</span><span class="sxs-lookup"><span data-stu-id="de2f4-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="de2f4-109">...</span><span class="sxs-lookup"><span data-stu-id="de2f4-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="de2f4-110">L’exemple de code-behind suivant gère les méthodes que le bouton <xref:System.Windows.Controls.Primitives.ButtonBase.Click> déclenche des événements.</span><span class="sxs-lookup"><span data-stu-id="de2f4-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="de2f4-111">L’exemple écrit les résultats de ces appels de méthode <xref:System.Windows.Controls.TextBlock> éléments liée de l’utilisation des méthodes get pour sortir les nouvelles valeurs de propriété sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="de2f4-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="de2f4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de2f4-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [<span data-ttu-id="de2f4-113">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="de2f4-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
