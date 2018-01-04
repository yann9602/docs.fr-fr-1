---
title: "Guide pratique pour implémenter une propriété de dépendance"
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
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d63e66b2458fa4ff21a227bdc2898d97e5eb30f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="0982e-102">Guide pratique pour implémenter une propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="0982e-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="0982e-103">Cet exemple montre comment sauvegarder un [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] propriété avec un <xref:System.Windows.DependencyProperty> champ, définissant ainsi une propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="0982e-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="0982e-104">Quand vous définissez vos propres propriétés et que vous souhaitez qu’elles prennent en charge de nombreux aspects des fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], notamment les styles, la liaison de données, l’héritage, l’animation et les valeurs par défaut, vous devez les implémenter en tant que propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="0982e-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0982e-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0982e-105">Example</span></span>  
 <span data-ttu-id="0982e-106">L’exemple suivant enregistre tout d’abord une propriété de dépendance en appelant le <xref:System.Windows.DependencyProperty.Register%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="0982e-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="0982e-107">Le nom du champ d’identificateur que vous utilisez pour stocker le nom et de caractéristiques de la propriété de dépendance doivent être le <xref:System.Windows.DependencyProperty.Name%2A> vous avez choisi pour la propriété de dépendance dans le cadre de la <xref:System.Windows.DependencyProperty.Register%2A> appel, ajouté par la chaîne littérale `Property`.</span><span class="sxs-lookup"><span data-stu-id="0982e-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="0982e-108">Par exemple, si vous inscrivez une propriété de dépendance avec un <xref:System.Windows.DependencyProperty.Name%2A> de `Location`, le champ d’identificateur que vous définissez pour la propriété de dépendance doit être nommé `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="0982e-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="0982e-109">Dans cet exemple, le nom de la propriété de dépendance et son [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accesseur est `State`; le champ d’identificateur est `StateProperty`; le type de la propriété est <xref:System.Boolean>; et le type qui inscrit la propriété de dépendance est `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="0982e-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="0982e-110">Si vous ne respectez pas ce modèle d’affectation de noms, les concepteurs risquent de ne pas signaler correctement votre propriété et certains aspects de l’application des styles du système de propriétés risquent de ne pas se comporter comme prévu.</span><span class="sxs-lookup"><span data-stu-id="0982e-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="0982e-111">Vous pouvez également spécifier des métadonnées par défaut pour une propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="0982e-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="0982e-112">Cet exemple inscrit `false` comme valeur par défaut de la propriété de dépendance `State`.</span><span class="sxs-lookup"><span data-stu-id="0982e-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="0982e-113">Pour plus d’informations sur la façon d’implémenter une propriété de dépendance et sur les raisons pour lesquelles vous devriez le faire, plutôt que de simplement stocker une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dans un champ privé, consultez [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0982e-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0982e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0982e-114">See Also</span></span>  
 [<span data-ttu-id="0982e-115">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="0982e-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="0982e-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="0982e-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
