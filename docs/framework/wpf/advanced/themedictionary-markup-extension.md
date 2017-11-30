---
title: ThemeDictionary, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f878ce89dcf76ae800ade10a0e67f019741f65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="themedictionary-markup-extension"></a><span data-ttu-id="7ba8e-102">ThemeDictionary, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="7ba8e-102">ThemeDictionary Markup Extension</span></span>
<span data-ttu-id="7ba8e-103">Cette extension offre un moyen aux auteurs de contrôles personnalisés ou aux applications qui intègrent des contrôles tiers de charger les dictionnaires de ressources de thème utilisés pour appliquer un style à un contrôle.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-103">Provides a way for custom control authors or applications that integrate third-party controls to load theme-specific resource dictionaries to use in styling the control.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7ba8e-104">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="7ba8e-104">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="7ba8e-105">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="7ba8e-105">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7ba8e-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="7ba8e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`assemblyUri`|<span data-ttu-id="7ba8e-107">[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de l’assembly qui contient des informations de thème.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-107">The [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] of the assembly that contains theme information.</span></span> <span data-ttu-id="7ba8e-108">Il s’agit généralement d’un URI à en-tête pack qui référence un assembly dans le package plus large.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-108">Typically, this is a pack URI that references an assembly in the larger package.</span></span> <span data-ttu-id="7ba8e-109">Les ressources d’assembly et les URI à en-tête pack simplifient le déploiement.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-109">Assembly resources and pack URIs simplify deployment issues.</span></span> <span data-ttu-id="7ba8e-110">Pour plus d’informations, consultez [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="7ba8e-110">For more information see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ba8e-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="7ba8e-111">Remarks</span></span>  
 <span data-ttu-id="7ba8e-112">Cette extension est conçue pour remplir une seule valeur de propriété spécifique : une valeur pour <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-112">This extension is intended to fill only one specific property value: a value for <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7ba8e-113">À l’aide de cette extension, vous pouvez spécifier un assembly de ressources uniquement qui contient des styles à utiliser uniquement quand le thème [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] est appliqué au système de l’utilisateur, d’autres styles à utiliser quand le thème Luna est appliqué, etc.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-113">By using this extension, you can specify a single resources-only assembly that contains some styles to use only when the [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] theme is applied to the user's system, other styles when Luna theme is active, and so on.</span></span> <span data-ttu-id="7ba8e-114">Quand vous utilisez cette extension, le contenu d’un dictionnaire de ressources d’un contrôle peut être automatiquement invalidé et rechargé pour un autre thème spécifique, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-114">By using this extension, the contents of a control-specific resource dictionary can be automatically invalidated and reloaded to be specific for another theme when required.</span></span>  
  
 <span data-ttu-id="7ba8e-115">Le `assemblyUri` chaîne (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> valeur de propriété) constitue la base d’une convention d’affectation de noms qui identifie le dictionnaire qui s’applique à un thème particulier.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-115">The `assemblyUri` string (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property value) forms the basis of a naming convention that identifies which dictionary applies for a particular theme.</span></span> <span data-ttu-id="7ba8e-116">Le <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logique pour `ThemeDictionary` complète la convention en générant un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] qui pointe sur une variante de dictionnaire thème particulier, contenue dans un assembly de ressources précompilé.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-116">The <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logic for `ThemeDictionary` completes the convention by generating a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that points to a particular theme dictionary variant, as contained within a precompiled resource assembly.</span></span> <span data-ttu-id="7ba8e-117">La description de cette convention, ou des interactions de thème à l’aide du style de contrôle général et du style de niveau page/application en tant que concept, n’est pas examinée de manière approfondie dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-117">Describing this convention, or theme interactions with general control styling and page/application level styling as a concept, is not covered fully here.</span></span> <span data-ttu-id="7ba8e-118">Le scénario de base pour l’utilisation de `ThemeDictionary` consiste à spécifier le <xref:System.Windows.ResourceDictionary.Source%2A> propriété d’un `ResourceDictionary` déclaré au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-118">The basic scenario for using `ThemeDictionary` is to specify the <xref:System.Windows.ResourceDictionary.Source%2A> property of a `ResourceDictionary` declared at the application level.</span></span> <span data-ttu-id="7ba8e-119">Quand vous fournissez un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour l’assembly par le biais d’une extension `ThemeDictionary` plutôt que directement avec un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], la logique d’extension fournit la logique d’invalidation qui s’applique chaque fois que le thème du système change.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-119">When you provide a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the assembly through a `ThemeDictionary` extension rather than as a direct [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], the extension logic will provide invalidation logic that applies whenever the system theme changes.</span></span>  
  
 <span data-ttu-id="7ba8e-120">La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-120">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="7ba8e-121">Le jeton de chaîne fourni après la chaîne d'identificateur `ThemeDictionary` est assigné en tant que valeur <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> de la classe d'extension <xref:System.Windows.ThemeDictionaryExtension> sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-121">The string token provided after the `ThemeDictionary` identifier string is assigned as the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> value of the underlying <xref:System.Windows.ThemeDictionaryExtension> extension class.</span></span>  
  
 <span data-ttu-id="7ba8e-122">`ThemeDictionary` peut également être utilisé dans la syntaxe de l’élément objet.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-122">`ThemeDictionary` may also be used in object element syntax.</span></span> <span data-ttu-id="7ba8e-123">Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> propriété est requise.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-123">In this case, specifying the value of the <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> property is required.</span></span>  
  
 <span data-ttu-id="7ba8e-124">`ThemeDictionary` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.Markup.StaticExtension.Member%2A> en tant que paire propriété=valeur :</span><span class="sxs-lookup"><span data-stu-id="7ba8e-124">`ThemeDictionary` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.Markup.StaticExtension.Member%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 <span data-ttu-id="7ba8e-125">L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-125">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="7ba8e-126">
          `ThemeDictionary` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-126">Because `ThemeDictionary` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="7ba8e-127">Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.ThemeDictionaryExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-127">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.ThemeDictionaryExtension> class.</span></span>  
  
 <span data-ttu-id="7ba8e-128">`ThemeDictionary` est une extension de balisage.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-128">`ThemeDictionary` is a markup extension.</span></span> <span data-ttu-id="7ba8e-129">Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-129">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="7ba8e-130">Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut.</span><span class="sxs-lookup"><span data-stu-id="7ba8e-130">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="7ba8e-131">Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="7ba8e-131">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba8e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ba8e-132">See Also</span></span>  
 [<span data-ttu-id="7ba8e-133">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="7ba8e-133">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7ba8e-134">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7ba8e-134">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="7ba8e-135">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="7ba8e-135">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="7ba8e-136">Fichiers de ressources, de contenu et de données d’une application WPF</span><span class="sxs-lookup"><span data-stu-id="7ba8e-136">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
