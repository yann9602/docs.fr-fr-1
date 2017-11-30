---
title: x:Shared, attribut
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d6a9333b2267e82fc25b2a0ec4bf5dd14f644078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xshared-attribute"></a><span data-ttu-id="59487-102">x:Shared, attribut</span><span class="sxs-lookup"><span data-stu-id="59487-102">x:Shared Attribute</span></span>
<span data-ttu-id="59487-103">Lorsque la valeur `false`, modifie le comportement de récupération des ressources WPF afin que les requêtes des ressources attribuées créent une nouvelle instance pour chaque demande au lieu de partager la même instance pour toutes les demandes.</span><span class="sxs-lookup"><span data-stu-id="59487-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="59487-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="59487-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="59487-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="59487-105">Remarks</span></span>  
 <span data-ttu-id="59487-106">`x:Shared`est mappé à l’espace de noms XAML du langage XAML et est reconnu comme un élément de langage XAML valid par les Services XAML .NET Framework et ses lecteurs XAML.</span><span class="sxs-lookup"><span data-stu-id="59487-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="59487-107">Toutefois, les fonctions déclarées de `x:Shared` sont uniquement pertinentes pour les applications WPF et pour l’analyseur XAML WPF.</span><span class="sxs-lookup"><span data-stu-id="59487-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="59487-108">Dans WPF, `x:Shared` n’est plus utile en tant qu’attribut lorsqu’il est appliqué à un objet qui existe dans WPF <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="59487-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="59487-109">Autres utilisations ne lèvent pas d’exceptions d’analyse ou d’autres erreurs, mais elles n’ont aucun effet.</span><span class="sxs-lookup"><span data-stu-id="59487-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="59487-110">La signification de `x:Shared` n’est pas spécifié dans la spécification du langage XAML.</span><span class="sxs-lookup"><span data-stu-id="59487-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="59487-111">Autres implémentations XAML, tels que ceux qui s’appuient sur les Services XAML .NET Framework, ne fournissent pas nécessairement le partage des ressources de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="59487-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="59487-112">Ces implémentations XAML peut fournir un comportement similaire dans l’infrastructure de prise en charge qui utilise également `x:Shared` valeurs.</span><span class="sxs-lookup"><span data-stu-id="59487-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="59487-113">Dans WPF, la valeur par défaut `x:Shared` condition de ressources est `true`.</span><span class="sxs-lookup"><span data-stu-id="59487-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="59487-114">Cette condition signifie que toute demande de ressource retourne toujours la même instance.</span><span class="sxs-lookup"><span data-stu-id="59487-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="59487-115">Modification d’un objet qui est retourné via une API de ressource telles que <xref:System.Windows.FrameworkElement.FindResource%2A>, ou la modification d’un objet directement au sein d’un <xref:System.Windows.ResourceDictionary>, la ressource d’origine change.</span><span class="sxs-lookup"><span data-stu-id="59487-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="59487-116">Si les références à cette ressource étaient des références de ressources dynamiques, les consommateurs de cette ressource obtiendront la ressource modifiée.</span><span class="sxs-lookup"><span data-stu-id="59487-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="59487-117">Si les références à la ressource étaient des références de ressources statiques, les modifications à la ressource après [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] le temps de traitement sont sans importance.</span><span class="sxs-lookup"><span data-stu-id="59487-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="59487-118">Pour plus d’informations sur les statiques et les références de ressources dynamiques, consultez [ressources XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="59487-118">For more information about static versus dynamic resource references, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="59487-119">Spécification explicite `x:Shared="true"` est rarement fait, car il s’agit déjà la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="59487-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="59487-120">S’il n’existe aucun code directe équivalent pour `x:Shared` modèle d’objet dans WPF ; il peut uniquement être spécifié dans une utilisation de XAML et doit être traité par le comportement WPF par défaut ou dans un flux de nœud XAML intermédiaire sur le chemin de chargement si traité à l’aide de .NET Framework XAML Se des services et ses lecteurs XAML.</span><span class="sxs-lookup"><span data-stu-id="59487-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="59487-121">Un scénario pour `x:Shared="false"` consiste à définir un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> dérivée de la classe en tant que ressource et puis vous introduisez la ressource d’élément dans un modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="59487-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="59487-122">`x:Shared="false"`permet à une ressource d’élément à introduire plusieurs fois dans la même collection (par exemple un <xref:System.Windows.Controls.UIElementCollection>).</span><span class="sxs-lookup"><span data-stu-id="59487-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="59487-123">Sans `x:Shared="false"` cela n’est pas valide, car la collection impose l’unicité de son contenu.</span><span class="sxs-lookup"><span data-stu-id="59487-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="59487-124">Toutefois, le `x:Shared="false"` comportement crée une autre instance identique de la ressource au lieu de retourner la même instance.</span><span class="sxs-lookup"><span data-stu-id="59487-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="59487-125">Un autre scénario de `x:Shared="false"` si vous utilisez un <xref:System.Windows.Freezable> ressource pour les valeurs d’animation, mais vous souhaitez modifier la ressource par animation.</span><span class="sxs-lookup"><span data-stu-id="59487-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="59487-126">La manipulation de chaînes `false` ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="59487-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="59487-127">Dans WPF, `x:Shared` n’est valide que dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="59487-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="59487-128">Le <xref:System.Windows.ResourceDictionary> qui contient les éléments avec `x:Shared` doit être compilé.</span><span class="sxs-lookup"><span data-stu-id="59487-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="59487-129">Le <xref:System.Windows.ResourceDictionary> ne peut pas être en XAML libre ou utilisé pour des thèmes.</span><span class="sxs-lookup"><span data-stu-id="59487-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="59487-130">Le <xref:System.Windows.ResourceDictionary> qui contient les éléments ne doit pas être imbriqué dans un autre <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="59487-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="59487-131">Par exemple, vous ne pouvez pas utiliser `x:Shared` pour les éléments dans un <xref:System.Windows.ResourceDictionary> qui se trouve dans un <xref:System.Windows.Style> qui est déjà un <xref:System.Windows.ResourceDictionary> élément.</span><span class="sxs-lookup"><span data-stu-id="59487-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59487-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59487-132">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="59487-133">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="59487-133">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="59487-134">Éléments de base</span><span class="sxs-lookup"><span data-stu-id="59487-134">Base Elements</span></span>](../../../docs/framework/wpf/advanced/base-elements.md)
