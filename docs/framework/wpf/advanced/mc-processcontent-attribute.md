---
title: mc:ProcessContent, attribut
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fe43e2450c35d976db7a188f854f7864f298afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="ab16b-102">mc:ProcessContent, attribut</span><span class="sxs-lookup"><span data-stu-id="ab16b-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="ab16b-103">Spécifie les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments doivent avoir toujours contenu traités par les éléments parents pertinents, même si l’élément parent immédiat peut être ignoré par un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur en raison de la spécification [mc : attribut Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="ab16b-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="ab16b-104">Le `mc:ProcessContent` attribut prend en charge la compatibilité du balisage à la fois pour le mappage d’espace de noms personnalisé et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="ab16b-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="ab16b-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="ab16b-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ab16b-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="ab16b-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab16b-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="ab16b-107">*ignorablePrefix*</span></span>|<span data-ttu-id="ab16b-108">Toute chaîne de préfixe valide, conformément à la spécification XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="ab16b-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="ab16b-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="ab16b-109">*ignorableUri*</span></span>|<span data-ttu-id="ab16b-110">Tout URI valide pour la désignation d’un espace de noms, conformément à la spécification XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="ab16b-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="ab16b-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="ab16b-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="ab16b-112">Un élément qui peut être ignoré par [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implémentations de processeur, si le type sous-jacent ne peut pas être résolu.</span><span class="sxs-lookup"><span data-stu-id="ab16b-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="ab16b-113">*[contenu]*</span><span class="sxs-lookup"><span data-stu-id="ab16b-113">*[content]*</span></span>|<span data-ttu-id="ab16b-114">*ThisElementCanBeIgnored* est marqué comme pouvant être ignoré.</span><span class="sxs-lookup"><span data-stu-id="ab16b-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="ab16b-115">Si le processeur ignore cet élément, *[contenu]* est traité par *objet*.</span><span class="sxs-lookup"><span data-stu-id="ab16b-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab16b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="ab16b-116">Remarks</span></span>  
 <span data-ttu-id="ab16b-117">Par défaut, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ignore le contenu d’un élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="ab16b-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="ab16b-118">Vous pouvez spécifier un élément spécifique par `mc:ProcessContent`et un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur continue à traiter le contenu dans l’élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="ab16b-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="ab16b-119">Cela doit généralement être utilisé si le contenu est imbriqué dans plusieurs balises, au moins un d'entre eux peut être ignoré et au moins un d'entre eux n’est pas peut être ignoré.</span><span class="sxs-lookup"><span data-stu-id="ab16b-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="ab16b-120">Plusieurs préfixes peuvent être spécifiés dans l’attribut, à l’aide d’un espace de séparation, par exemple : `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="ab16b-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="ab16b-121">Le [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] espace de noms définit d’autres éléments et attributs qui ne sont pas documentés dans cette zone de la [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab16b-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="ab16b-122">Pour plus d’informations, consultez [spécification de compatibilité du balisage XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="ab16b-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab16b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab16b-123">See Also</span></span>  
 [<span data-ttu-id="ab16b-124">mc:Ignorable, attribut</span><span class="sxs-lookup"><span data-stu-id="ab16b-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="ab16b-125">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="ab16b-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
