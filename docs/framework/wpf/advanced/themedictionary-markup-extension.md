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
ms.workload: dotnet
ms.openlocfilehash: 2372961cdc889528f13e13dd1f1760608030275e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary, extension de balisage
Cette extension offre un moyen aux auteurs de contrôles personnalisés ou aux applications qui intègrent des contrôles tiers de charger les dictionnaires de ressources de thème utilisés pour appliquer un style à un contrôle.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de l’assembly qui contient des informations de thème. Il s’agit généralement d’un URI à en-tête pack qui référence un assembly dans le package plus large. Les ressources d’assembly et les URI à en-tête pack simplifient le déploiement. Pour plus d’informations, consultez [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Notes  
 Cette extension est conçue pour remplir une seule valeur de propriété spécifique : une valeur pour <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 À l’aide de cette extension, vous pouvez spécifier un assembly de ressources uniquement qui contient des styles à utiliser uniquement quand le thème [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] est appliqué au système de l’utilisateur, d’autres styles à utiliser quand le thème Luna est appliqué, etc. Quand vous utilisez cette extension, le contenu d’un dictionnaire de ressources d’un contrôle peut être automatiquement invalidé et rechargé pour un autre thème spécifique, si nécessaire.  
  
 Le `assemblyUri` chaîne (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> valeur de propriété) constitue la base d’une convention d’affectation de noms qui identifie le dictionnaire qui s’applique à un thème particulier. Le <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> logique pour `ThemeDictionary` complète la convention en générant un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] qui pointe sur une variante de dictionnaire thème particulier, contenue dans un assembly de ressources précompilé. La description de cette convention, ou des interactions de thème à l’aide du style de contrôle général et du style de niveau page/application en tant que concept, n’est pas examinée de manière approfondie dans cette rubrique. Le scénario de base pour l’utilisation de `ThemeDictionary` consiste à spécifier le <xref:System.Windows.ResourceDictionary.Source%2A> propriété d’un `ResourceDictionary` déclaré au niveau de l’application. Quand vous fournissez un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour l’assembly par le biais d’une extension `ThemeDictionary` plutôt que directement avec un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], la logique d’extension fournit la logique d’invalidation qui s’applique chaque fois que le thème du système change.  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d'identificateur `ThemeDictionary` est assigné en tant que valeur <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> de la classe d'extension <xref:System.Windows.ThemeDictionaryExtension> sous-jacente.  
  
 `ThemeDictionary` peut également être utilisé dans la syntaxe de l’élément objet. Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> propriété est requise.  
  
 `ThemeDictionary` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.Markup.StaticExtension.Member%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. 
          `ThemeDictionary` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.ThemeDictionaryExtension> classe.  
  
 `ThemeDictionary` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Fichiers de ressources, de contenu et de données d’une application WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
