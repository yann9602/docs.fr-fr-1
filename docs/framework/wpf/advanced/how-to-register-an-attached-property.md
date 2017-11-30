---
title: "Guide pratique pour inscrire une propriété jointe"
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
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aecb5d2f35b8532ad2ae7558af1a93243b0fd6df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="6b417-102">Guide pratique pour inscrire une propriété jointe</span><span class="sxs-lookup"><span data-stu-id="6b417-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="6b417-103">Cet exemple montre comment inscrire une propriété jointe et fournir des accesseurs publics pour pouvoir utiliser la propriété en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et dans le code.</span><span class="sxs-lookup"><span data-stu-id="6b417-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="6b417-104">Les propriétés jointes sont un concept de syntaxe défini par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b417-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="6b417-105">La plupart des propriétés jointes pour les types [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont également implémentées en tant que propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="6b417-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="6b417-106">Vous pouvez utiliser les propriétés de dépendance sur n’importe quel <xref:System.Windows.DependencyObject> types.</span><span class="sxs-lookup"><span data-stu-id="6b417-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b417-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b417-107">Example</span></span>  
 <span data-ttu-id="6b417-108">L’exemple suivant montre comment inscrire une propriété jointe comme une propriété de dépendance à l’aide de la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6b417-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="6b417-109">La classe de fournisseur a la possibilité de fournir des métadonnées par défaut pour la propriété qui s’appliquent quand celle-ci est utilisée sur une autre classe, à moins que cette classe ne substitue les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6b417-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="6b417-110">Dans cet exemple, la valeur par défaut de la propriété `IsBubbleSource` est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="6b417-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="6b417-111">La classe de fournisseur pour une propriété jointe (même si elle n’est pas inscrite en tant que propriété de dépendance) doit fournir des accesseurs get et set statiques qui respectent la convention d’affectation de noms `Set`*[NomPropriétéJointe]* et `Get`*[NomPropriétéJointe]*.</span><span class="sxs-lookup"><span data-stu-id="6b417-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="6b417-112">Ces accesseurs sont nécessaires pour que le lecteur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] puisse reconnaître la propriété en tant qu’attribut en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et résoudre les types appropriés.</span><span class="sxs-lookup"><span data-stu-id="6b417-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="6b417-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b417-113">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="6b417-114">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="6b417-114">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="6b417-115">Propriétés de dépendance personnalisées</span><span class="sxs-lookup"><span data-stu-id="6b417-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="6b417-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="6b417-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
