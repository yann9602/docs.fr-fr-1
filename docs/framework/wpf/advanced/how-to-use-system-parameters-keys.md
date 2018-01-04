---
title: "Guide pratique pour utiliser les clés des paramètres système"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b2a7352540456b459428dd87f6c60be0b8bc08b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="b1f48-102">Guide pratique pour utiliser les clés des paramètres système</span><span class="sxs-lookup"><span data-stu-id="b1f48-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="b1f48-103">Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels cohérents avec les paramètres système.</span><span class="sxs-lookup"><span data-stu-id="b1f48-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="b1f48-104"><xref:System.Windows.SystemParameters>est une classe qui contient les valeurs de paramètre système et des clés de ressources liées aux valeurs, par exemple, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> et <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1f48-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="b1f48-105">Les métriques de paramètres système peuvent être utilisées en tant que ressources statiques ou dynamiques.</span><span class="sxs-lookup"><span data-stu-id="b1f48-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="b1f48-106">Utilisez une ressource dynamique si vous souhaitez que les métriques de paramètres soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une ressource statique.</span><span class="sxs-lookup"><span data-stu-id="b1f48-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1f48-107">Ressources dynamiques ont le mot clé *clé* ajouté au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="b1f48-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="b1f48-108">L’exemple suivant montre comment accéder à des ressources dynamiques de paramètres système et comment les utiliser pour personnaliser un bouton ou lui appliquer un style.</span><span class="sxs-lookup"><span data-stu-id="b1f48-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="b1f48-109">Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemple dimensionne un bouton en assignant <xref:System.Windows.SystemParameters> valeurs à la largeur et la hauteur du bouton.</span><span class="sxs-lookup"><span data-stu-id="b1f48-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f48-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1f48-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="b1f48-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1f48-111">See Also</span></span>  
 [<span data-ttu-id="b1f48-112">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="b1f48-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="b1f48-113">Utiliser des SystemFonts</span><span class="sxs-lookup"><span data-stu-id="b1f48-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="b1f48-114">Utiliser SystemParameters</span><span class="sxs-lookup"><span data-stu-id="b1f48-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
