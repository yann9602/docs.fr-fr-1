---
title: mc:Ignorable, attribut
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be5949ee26fbb21d913a7aefe2664202c5bef38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mcignorable-attribute"></a><span data-ttu-id="7b7da-102">mc:Ignorable, attribut</span><span class="sxs-lookup"><span data-stu-id="7b7da-102">mc:Ignorable Attribute</span></span>
<span data-ttu-id="7b7da-103">Spécifie les [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les préfixes d’espace de noms rencontrés dans un fichier de balisage peuvent être ignorés par un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur.</span><span class="sxs-lookup"><span data-stu-id="7b7da-103">Specifies which [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefixes encountered in a markup file may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="7b7da-104">Le `mc:Ignorable` attribut prend en charge la compatibilité du balisage à la fois pour le mappage d’espace de noms personnalisé et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="7b7da-104">The `mc:Ignorable` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage-single-prefix"></a><span data-ttu-id="7b7da-105">Utilisation d’attributs XAML (un seul préfixe)</span><span class="sxs-lookup"><span data-stu-id="7b7da-105">XAML Attribute Usage (Single Prefix)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a><span data-ttu-id="7b7da-106">Utilisation d’attributs XAML (deux préfixes)</span><span class="sxs-lookup"><span data-stu-id="7b7da-106">XAML Attribute Usage (Two Prefixes)</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7b7da-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="7b7da-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b7da-108">*ignorablePrefix, ignorablePrefix1, etc.*</span><span class="sxs-lookup"><span data-stu-id="7b7da-108">*ignorablePrefix, ignorablePrefix1, etc.*</span></span>|<span data-ttu-id="7b7da-109">Toute chaîne de préfixe valide, conformément à la spécification XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="7b7da-109">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="7b7da-110">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="7b7da-110">*ignorableUri*</span></span>|<span data-ttu-id="7b7da-111">Tout URI valide pour la désignation d’un espace de noms, conformément à la spécification XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="7b7da-111">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="7b7da-112">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="7b7da-112">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="7b7da-113">Un élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implémentations de processeur, si le type sous-jacent ne peut pas être résolu.</span><span class="sxs-lookup"><span data-stu-id="7b7da-113">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b7da-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="7b7da-114">Remarks</span></span>  
 <span data-ttu-id="7b7da-115">Le `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] préfixe d’espace de noms est la convention de préfixe recommandé à utiliser lors du mappage de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] espace de noms de compatibilité [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b7da-115">The `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace prefix is the recommended prefix convention to use when mapping the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compatibility namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].</span></span>  
  
 <span data-ttu-id="7b7da-116">Éléments ou attributs où le préfixe de nom de l’élément sont identifiés comme `mc:Ignorable` ne génère pas d’erreurs lors du traitement par un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur.</span><span class="sxs-lookup"><span data-stu-id="7b7da-116">Elements or attributes where the prefix portion of the element name are identified as `mc:Ignorable` will not raise errors when processed by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor.</span></span> <span data-ttu-id="7b7da-117">Si cet attribut n’a pas pu être résolu en un type sous-jacent ou une construction de programmation, cet élément est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7b7da-117">If that attribute could not be resolved to an underlying type or programming construct, then that element is ignored.</span></span> <span data-ttu-id="7b7da-118">Notez toutefois que les éléments ignorés peuvent générer des erreurs d’analyse supplémentaires pour les spécifications d’élément supplémentaires qui sont des effets de l’élément n’est pas traitée.</span><span class="sxs-lookup"><span data-stu-id="7b7da-118">Note however that ignored elements might still generate additional parsing errors for additional element requirements that are side effects of that element not being processed.</span></span> <span data-ttu-id="7b7da-119">Par exemple, un modèle de contenu d’élément particulier peut nécessiter un seul élément enfant, mais si l’élément enfant spécifié était dans un `mc:Ignorable` préfixe et l’élément enfant spécifié n’a pas pu être résolue en un type, puis le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur peut génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="7b7da-119">For instance, a particular element content model might require exactly one child element, but if the specified child element was in an `mc:Ignorable` prefix, and the specified child element could not be resolved to a type, then the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor might raise an error.</span></span>  
  
 <span data-ttu-id="7b7da-120">`mc:Ignorable`s’applique uniquement aux mappages d’espace de noms pour les chaînes d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="7b7da-120">`mc:Ignorable` only applies to namespace mappings to identifier strings.</span></span> <span data-ttu-id="7b7da-121">`mc:Ignorable`ne s’applique pas aux mappages d’espace de noms dans les assemblys, qui spécifient un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] espace de noms et un assembly (ou la valeur par défaut pour le fichier exécutable actuel en tant que l’assembly).</span><span class="sxs-lookup"><span data-stu-id="7b7da-121">`mc:Ignorable` does not apply to namespace mappings into assemblies, which specify a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace and an assembly (or default to the current executable as the assembly).</span></span>  
  
 <span data-ttu-id="7b7da-122">Si vous implémentez un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur, votre implémentation de processeur ne doit pas déclencher l’analyse ou de traitement des erreurs sur la résolution de type pour tout élément ou attribut qualifié par un préfixe qui est identifié en tant que `mc:Ignorable`.</span><span class="sxs-lookup"><span data-stu-id="7b7da-122">If you are implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor, your processor implementation must not raise parsing or processing errors on type resolution for any element or attribute that is qualified by a prefix that is identified as `mc:Ignorable`.</span></span> <span data-ttu-id="7b7da-123">Mais votre implémentation de processeur peut toujours lever les exceptions sont le résultat d’un élément ne peut pas charger ou être traitées, comme l’exemple d’élément enfant de celui donné précédemment secondaire.</span><span class="sxs-lookup"><span data-stu-id="7b7da-123">But your processor implementation can still raise exceptions that are a secondary result of an element failing to load or be processed, such as the one-child element example given earlier.</span></span>  
  
 <span data-ttu-id="7b7da-124">Par défaut, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ignore le contenu d’un élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="7b7da-124">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="7b7da-125">Toutefois, vous pouvez spécifier un attribut supplémentaire, [MC : ProcessContent attribut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), afin de demander la poursuite du traitement du contenu d’un élément ignoré par l’élément parent disponible suivant.</span><span class="sxs-lookup"><span data-stu-id="7b7da-125">However, you can specify an additional attribute, [mc:ProcessContent Attribute](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), to require continued processing of content within an ignored element by the next available parent element.</span></span>  
  
 <span data-ttu-id="7b7da-126">Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un ou plusieurs caractères d’espace comme séparateur, par exemple : `mc:Ignorable="ignore1 ignore2"`.</span><span class="sxs-lookup"><span data-stu-id="7b7da-126">Multiple prefixes can be specified in the attribute, using one or more whitespace characters as the separator, for example: `mc:Ignorable="ignore1 ignore2"`.</span></span>  
  
 <span data-ttu-id="7b7da-127">Le [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] espace de noms définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone de la [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b7da-127">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="7b7da-128">Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="7b7da-128">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7da-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b7da-129">See Also</span></span>  
 <xref:System.Windows.Markup.XamlReader>  
 [<span data-ttu-id="7b7da-130">PresentationOptions:Freeze, attribut</span><span class="sxs-lookup"><span data-stu-id="7b7da-130">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [<span data-ttu-id="7b7da-131">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7b7da-131">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="7b7da-132">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="7b7da-132">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
