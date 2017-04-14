---
title: "x:Null Markup Extension | Microsoft Docs"
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
  - "NullExtension"
  - "x:NullExtension"
  - "x:Null"
  - "Null"
  - "xNull"
helpviewer_keywords: 
  - "Null markup extension in XAML [XAML Services]"
  - "x:Null markup extension [XAML Services]"
  - "XAML [XAML Services], x:Null markup extension"
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Null Markup Extension
Spécifie `null` comme valeur pour un membre XAML.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{x:Null}" .../>  
```  
  
## Notes  
 Le mot clé pour une référence null dans [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] et [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] est null.  Le mot clé [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] d'une référence null est `Nothing`, mais vous utilisez toujours `{x:Null}` comme utilisation de XAML, quel que soit le langage code\-behind associé au XAML.  
  
 L'extension de balisage `x:Null` n'a pas de propriétés définissables.  
  
 Une utilisation null est souvent associée à l'exposition des membres XAML d'une valeur CLR <xref:System.Nullable%601>.  
  
 L'extension de balisage `x:Null`, comme toutes les extensions de balisage XAML, utilise l'accolade \(`{,}`\) pour placer dans une séquence d'échappement la gestion de valeurs d'attribut afin qu'elles soient autre chose que des littéraux ou des références de gestionnaire d'événements.  La syntaxe d'attribut est la syntaxe la plus souvent utilisée avec cette extension de balisage.  Une syntaxe d'élément objet `<x:Null />` est techniquement possible, mais elle est rarement utilisée parce que l'extension de balisage `x:Null` n'a pas de paramètres positionnels ni d'arguments de construction.  
  
 Pour plus d'informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Dans les services XAML .NET Framework, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.NullExtension>.  
  
## Remarques sur l'utilisation de WPF  
 Notez que `null` n'est pas nécessairement la valeur initiale non définie d'une propriété de dépendance de type référence.  La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur les métadonnées spécifiques à la propriété.  De nombreuses propriétés de dépendance n'accepteront pas `null` comme valeur, via une balise ou du code, en raison de leurs implémentations de rappel de validation.  Pour plus d'informations sur les propriétés de dépendance, consultez [Vue d'ensemble des propriétés de dépendance](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## Voir aussi  
 <xref:System.Windows.DependencyProperty.UnsetValue>   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)