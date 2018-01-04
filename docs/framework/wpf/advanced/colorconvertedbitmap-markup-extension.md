---
title: ColorConvertedBitmap, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df6fac332f20d64ddf6569554a75ef96a5536c0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="210f5-102">ColorConvertedBitmap, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="210f5-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="210f5-103">Fournit un moyen de spécifier une image bitmap source qui n’a pas de profil incorporé.</span><span class="sxs-lookup"><span data-stu-id="210f5-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="210f5-104">Couleur des contextes / profils sont spécifiées par [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], comme l’image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="210f5-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="210f5-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="210f5-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="210f5-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="210f5-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="210f5-107">Le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de l’image bitmap non profilée.</span><span class="sxs-lookup"><span data-stu-id="210f5-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="210f5-108">Le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la configuration du profil source.</span><span class="sxs-lookup"><span data-stu-id="210f5-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="210f5-109">Le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la configuration de profil de destination</span><span class="sxs-lookup"><span data-stu-id="210f5-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="210f5-110">Notes</span><span class="sxs-lookup"><span data-stu-id="210f5-110">Remarks</span></span>  
 <span data-ttu-id="210f5-111">Cette extension de balisage est conçue pour remplir un ensemble de valeurs de propriété de source de l’image de telles que <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="210f5-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="210f5-112">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="210f5-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="210f5-113">`ColorConvertedBitmap`(ou `ColorConvertedBitmapExtension`) ne peut pas être utilisé dans la syntaxe d’élément de propriété, car les valeurs peuvent uniquement être définies en tant que valeurs dans le constructeur initial, qui est la chaîne suivante de l’identificateur d’extension.</span><span class="sxs-lookup"><span data-stu-id="210f5-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="210f5-114">`ColorConvertedBitmap` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="210f5-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="210f5-115">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="210f5-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="210f5-116">Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="210f5-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="210f5-117">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="210f5-117">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210f5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="210f5-118">See Also</span></span>  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [<span data-ttu-id="210f5-119">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="210f5-119">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="210f5-120">Vue d’ensemble de la création d’images</span><span class="sxs-lookup"><span data-stu-id="210f5-120">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
