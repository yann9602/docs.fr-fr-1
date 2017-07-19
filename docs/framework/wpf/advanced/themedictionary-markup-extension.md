---
title: "ThemeDictionary, extension de balisage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ThemeDictionaryExtension"
  - "ThemeDictionary"
helpviewer_keywords: 
  - "ThemeDictionary (extension de balisage)"
  - "XAML, ThemeDictionary (extension de balisage)"
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ThemeDictionary, extension de balisage
Offre un moyen aux auteurs de contrôles personnalisés ou aux applications qui intègrent des contrôles tiers de charger des dictionnaires de ressources spécifiques aux thèmes afin de définir le style du contrôle.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## Utilisation d'éléments objet XAML  
  
```  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de l'assembly qui contient des informations sur les thèmes.  Il s'agit généralement d'un URI à en\-tête pack qui référence un assembly dans le package plus large.  Les ressources d'assembly et les URI à en\-tête pack simplifient les problèmes de déploiement.  Pour plus d'informations, consultez [URI à en\-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## Notes  
 Cette extension est conçue pour remplir une seule valeur de propriété spécifique : une valeur pour <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=fullName>.  
  
 En utilisant cette extension, vous pouvez spécifier un assembly de ressources uniquement contenant des styles à utiliser que lorsque le thème [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] est appliqué au système de l'utilisateur, d'autres styles à utiliser lorsque le thème Luna est actif, etc.  Lorsque vous utilisez cette extension, le contenu d'un dictionnaire de ressources spécifique au contrôle peut être automatiquement invalidé et rechargé pour être spécifique à un autre thème si nécessaire.  
  
 La chaîne `assemblyUri` \(valeur de propriété <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>\) sert de base à une convention d'affectation de noms qui identifie le dictionnaire qui s'applique à un thème particulier.  La logique <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> du `ThemeDictionary` complète la convention en générant un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] qui pointe sur une variante particulière du dictionnaire de thèmes, contenue dans un assembly de ressources précompilé.  La description de cette convention ou des interactions de thème à l'aide du style de contrôle général et du style de niveau page\/application en tant que concept n'est pas examinée de manière approfondie dans cette rubrique.  Le scénario de base pour l'utilisation du `ThemeDictionary` consiste à spécifier la propriété <xref:System.Windows.ResourceDictionary.Source%2A> d'un `ResourceDictionary` déclaré au niveau de l'application.  Lorsque vous fournissez un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour l'assembly par le biais d'une extension `ThemeDictionary` plutôt que sous la forme d'un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] direct, la logique d'extension fournit la logique d'invalidation qui s'applique chaque fois que le thème du système change.  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  Le jeton de chaîne fourni après la chaîne d'identificateur `ThemeDictionary` est assigné en tant que valeur <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> de la classe d'extension <xref:System.Windows.ThemeDictionaryExtension> sous\-jacente.  
  
 `ThemeDictionary` peut également être utilisé dans la syntaxe d'élément objet.  Dans ce cas, la valeur de la propriété <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> doit être spécifiée.  
  
 `ThemeDictionary` peut également être employé dans une utilisation d'attribut en clair qui spécifie la propriété <xref:System.Windows.Markup.StaticExtension.Member%2A> en tant que paire propriété\=valeur :  
  
```  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.  `ThemeDictionary` ne comportant qu'une seule propriété définissable \(obligatoire\), cette utilisation en clair n'est pas classique.  
  
 Dans l'implémentation de processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.ThemeDictionaryExtension>.  
  
 `ThemeDictionary` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  Toutes les extensions de balisage en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d'attributs. Cette convention indique au convertisseur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que l'extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Fichiers de ressources, de contenu et de données d'une application WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)