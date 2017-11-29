---
title: "Comment : ajouter un type propriétaire d'une propriété de dépendance"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 079f08e1c330b710748ea6bb1aab8ccfb7ae7016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="cd689-102">Comment : ajouter un type propriétaire d'une propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="cd689-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="cd689-103">Cet exemple montre comment ajouter une classe en tant que propriétaire d’une propriété de dépendance inscrite pour un type différent.</span><span class="sxs-lookup"><span data-stu-id="cd689-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="cd689-104">Ainsi, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] du lecteur et système de propriétés sont en mesure de reconnaître la classe en tant que propriétaire de la propriété supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="cd689-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="cd689-105">Ajout en tant que propriétaire éventuellement permet de la classe d’ajout fournir les métadonnées spécifiques au type.</span><span class="sxs-lookup"><span data-stu-id="cd689-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="cd689-106">Dans l’exemple suivant, `StateProperty` est une propriété inscrite par la `MyStateControl` classe.</span><span class="sxs-lookup"><span data-stu-id="cd689-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="cd689-107">La classe `UnrelatedStateControl` ajoute lui-même en tant que propriétaire de la `StateProperty` à l’aide de la <xref:System.Windows.DependencyProperty.AddOwner%2A> méthode, en particulier à l’aide de la signature qui permet de nouvelles métadonnées de la propriété de dépendance telle qu’elle existe sur le type d’ajout.</span><span class="sxs-lookup"><span data-stu-id="cd689-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="cd689-108">Notez que vous devez fournir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accesseurs de la propriété semblable à l’exemple illustré dans la [implémenter une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) exemple, ainsi que de nouveau exposer l’identificateur de propriété de dépendance dans la classe ajoutée en tant que propriétaire.</span><span class="sxs-lookup"><span data-stu-id="cd689-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="cd689-109">Sans wrappers, la propriété de dépendance continuerait de fonctionner du point de vue de l’accès par programme à l’aide <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd689-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="cd689-110">Mais vous souhaiterez généralement parallèlement ce comportement de système de propriétés avec le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] wrappers de propriété.</span><span class="sxs-lookup"><span data-stu-id="cd689-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="cd689-111">Les wrappers rendre plus facile de définir la propriété de dépendance par programme et permettent de définir les propriétés comme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributs.</span><span class="sxs-lookup"><span data-stu-id="cd689-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="cd689-112">Pour savoir comment remplacer les métadonnées par défaut, consultez [remplacer les métadonnées pour une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="cd689-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd689-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd689-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="cd689-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd689-114">See Also</span></span>  
 [<span data-ttu-id="cd689-115">Propriétés de dépendance personnalisées</span><span class="sxs-lookup"><span data-stu-id="cd689-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="cd689-116">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="cd689-116">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
