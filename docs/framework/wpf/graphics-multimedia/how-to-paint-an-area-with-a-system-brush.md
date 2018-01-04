---
title: "Comment : peindre une zone avec un pinceau système"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87979c16d52262c665e2fb37fdf6d7550c5930c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="d73e5-102">Comment : peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="d73e5-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="d73e5-103">Le <xref:System.Windows.SystemColors> classe fournit l’accès aux pinceaux système et couleurs, tel que <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, et <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="d73e5-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="d73e5-104">Un pinceau système est un <xref:System.Windows.Media.SolidColorBrush> objet qui peint une zone avec la couleur système spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d73e5-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="d73e5-105">Un pinceau système produit toujours un remplissage uni ; vous ne pouvez pas l’utiliser pour créer un dégradé.</span><span class="sxs-lookup"><span data-stu-id="d73e5-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="d73e5-106">Vous pouvez utiliser des pinceaux système comme ressource dynamique ou statique.</span><span class="sxs-lookup"><span data-stu-id="d73e5-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="d73e5-107">Utilisez une ressource dynamique si vous souhaitez que le pinceau soit automatiquement mis à jour si l’utilisateur modifie le pinceau système alors que l’application est en cours d’exécution ; sinon, utilisez une ressource statique.</span><span class="sxs-lookup"><span data-stu-id="d73e5-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="d73e5-108">La classe SystemColors contient diverses propriétés statiques qui suivent une convention d’affectation de noms stricte :</span><span class="sxs-lookup"><span data-stu-id="d73e5-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="d73e5-109">*\<SystemColor>*Brush</span><span class="sxs-lookup"><span data-stu-id="d73e5-109">*\<SystemColor>*Brush</span></span>  
  
     <span data-ttu-id="d73e5-110">Obtient une référence statique à un <xref:System.Windows.Media.SolidColorBrush> de la couleur système spécifié.</span><span class="sxs-lookup"><span data-stu-id="d73e5-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="d73e5-111">*\<SystemColor>*BrushKey</span><span class="sxs-lookup"><span data-stu-id="d73e5-111">*\<SystemColor>*BrushKey</span></span>  
  
     <span data-ttu-id="d73e5-112">Obtient une référence dynamique à un <xref:System.Windows.Media.SolidColorBrush> de la couleur système spécifié.</span><span class="sxs-lookup"><span data-stu-id="d73e5-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="d73e5-113">*\<SystemColor>*Color</span><span class="sxs-lookup"><span data-stu-id="d73e5-113">*\<SystemColor>*Color</span></span>  
  
     <span data-ttu-id="d73e5-114">Obtient une référence statique à un <xref:System.Windows.Media.Color> structure de la couleur système spécifié.</span><span class="sxs-lookup"><span data-stu-id="d73e5-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="d73e5-115">*\<SystemColor>*ColorKey</span><span class="sxs-lookup"><span data-stu-id="d73e5-115">*\<SystemColor>*ColorKey</span></span>  
  
     <span data-ttu-id="d73e5-116">Obtient une référence dynamique à la <xref:System.Windows.Media.Color> structure de la couleur système spécifié.</span><span class="sxs-lookup"><span data-stu-id="d73e5-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="d73e5-117">Une couleur système est un <xref:System.Windows.Media.Color> structure peut être utilisé pour configurer un pinceau.</span><span class="sxs-lookup"><span data-stu-id="d73e5-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="d73e5-118">Par exemple, vous pouvez créer un dégradé à l’aide de couleurs système en définissant le <xref:System.Windows.Media.GradientStop.Color%2A> propriétés d’un <xref:System.Windows.Media.LinearGradientBrush> de dégradé de l’objet avec les couleurs système.</span><span class="sxs-lookup"><span data-stu-id="d73e5-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="d73e5-119">Pour obtenir un exemple, consultez [utiliser des couleurs système dans un dégradé](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="d73e5-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d73e5-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="d73e5-120">Example</span></span>  
 <span data-ttu-id="d73e5-121">L’exemple suivant utilise une référence de pinceau système dynamique pour définir l’arrière-plan d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="d73e5-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="d73e5-122">L’exemple suivant utilise une référence de pinceau système statique pour définir l’arrière-plan d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="d73e5-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="d73e5-123">Pour obtenir un exemple montrant comment utiliser une couleur système dans un dégradé, consultez [utiliser les couleurs système dans un dégradé](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="d73e5-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73e5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d73e5-124">See Also</span></span>  
 [<span data-ttu-id="d73e5-125">Utiliser des couleurs système dans un dégradé</span><span class="sxs-lookup"><span data-stu-id="d73e5-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="d73e5-126">Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="d73e5-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
