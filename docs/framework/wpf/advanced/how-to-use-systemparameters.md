---
title: Guide pratique pour utiliser SystemParameters
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
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec333fbc30374ff6f8e2e7674ab332644ff7aad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="1dc9d-102">Guide pratique pour utiliser SystemParameters</span><span class="sxs-lookup"><span data-stu-id="1dc9d-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="1dc9d-103">Cet exemple montre comment accéder à et utiliser les propriétés de <xref:System.Windows.SystemParameters> afin d’appliquer un style ou personnaliser un bouton.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dc9d-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1dc9d-104">Example</span></span>  
 <span data-ttu-id="1dc9d-105">Les ressources système exposent plusieurs paramètres système en tant que ressources pour vous aider à créer des visuels cohérents avec les paramètres système.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="1dc9d-106"><xref:System.Windows.SystemParameters>est une classe qui contient à la fois des propriétés de valeur de paramètre système et des clés de ressources liées aux valeurs.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="1dc9d-107">Par exemple, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> est un <xref:System.Windows.SystemParameters> valeur de propriété et <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> est la clé de ressource correspondante.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="1dc9d-108">Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemParameters> comme utilisation de propriété statique ou un fait référence à une ressource dynamique (avec la valeur de propriété statique en tant que la clé).</span><span class="sxs-lookup"><span data-stu-id="1dc9d-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="1dc9d-109">Utilisez une référence de ressource dynamique si vous souhaitez que la valeur système soit mise à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une référence statique.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="1dc9d-110">Les clés de ressources ont le suffixe `Key` ajouté au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="1dc9d-111">L’exemple suivant montre comment accéder à et utiliser des valeurs statiques de <xref:System.Windows.SystemParameters> pour appliquer un style ou personnaliser un bouton.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="1dc9d-112">Cet exemple de balisage dimensionne un bouton en appliquant <xref:System.Windows.SystemParameters> valeurs à un bouton.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="1dc9d-113">Pour utiliser les valeurs de <xref:System.Windows.SystemParameters> dans le code, vous n’avez pas à utiliser des références statiques ou références de ressources dynamiques.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="1dc9d-114">Au lieu de cela, utilisez les valeurs de la <xref:System.Windows.SystemParameters> classe.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="1dc9d-115">Bien que les propriétés non clé soient apparemment définies en tant que propriétés statiques, le comportement d’exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comme hébergé par le système sera réévalue les propriétés en temps réel, et tient compte des modifications utilisateur apportées aux valeurs système.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="1dc9d-116">L’exemple suivant montre comment définir la largeur et la hauteur d’un bouton à l’aide de <xref:System.Windows.SystemParameters> valeurs.</span><span class="sxs-lookup"><span data-stu-id="1dc9d-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="1dc9d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dc9d-117">See Also</span></span>  
 <xref:System.Windows.SystemParameters>  
 [<span data-ttu-id="1dc9d-118">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="1dc9d-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="1dc9d-119">Utiliser des SystemFonts</span><span class="sxs-lookup"><span data-stu-id="1dc9d-119">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="1dc9d-120">Utiliser les clés des paramètres système</span><span class="sxs-lookup"><span data-stu-id="1dc9d-120">Use System Parameters Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [<span data-ttu-id="1dc9d-121">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="1dc9d-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
