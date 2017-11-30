---
title: "Guide pratique pour utiliser des clés de polices système"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18781e3d71b9b30352323081e6d938350c6e53d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="cd3b1-102">Guide pratique pour utiliser des clés de polices système</span><span class="sxs-lookup"><span data-stu-id="cd3b1-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="cd3b1-103">Les ressources système exposent plusieurs métriques système en tant que ressources pour aider les développeurs à créer des visuels cohérents avec les paramètres système.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="cd3b1-104"><xref:System.Windows.SystemFonts>est une classe qui contient des valeurs de police système et des ressources de police système liées aux valeurs, par exemple, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> et <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="cd3b1-105">Les métriques de police système peuvent être utilisées en tant que ressources statiques ou dynamiques.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="cd3b1-106">Utilisez une ressource dynamique si vous souhaitez que les métriques de police soient mises à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une ressource statique.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd3b1-107">Ressources dynamiques ont le mot clé *clé* ajouté au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="cd3b1-108">L’exemple suivant montre comment accéder à des ressources dynamiques de police système et comment les utiliser pour personnaliser un bouton ou lui appliquer un style.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="cd3b1-109">Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemple crée un style de bouton qui assigne <xref:System.Windows.SystemFonts> valeurs à un bouton.</span><span class="sxs-lookup"><span data-stu-id="cd3b1-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd3b1-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd3b1-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="cd3b1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd3b1-111">See Also</span></span>  
 [<span data-ttu-id="cd3b1-112">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="cd3b1-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="cd3b1-113">Utiliser SystemParameters</span><span class="sxs-lookup"><span data-stu-id="cd3b1-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="cd3b1-114">Utiliser des SystemFonts</span><span class="sxs-lookup"><span data-stu-id="cd3b1-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
