---
title: "xml:lang Handling in XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML [XAML Services], xml:lang attribute"
  - "xml:lang attribute [XAML Services]"
  - "RFC 3066 standard [XAML Services]"
  - "standards [XAML Services], RFC 3066"
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: 16
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 15
---
# xml:lang Handling in XAML
L’attribut `xml:lang` est un attribut [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] qui déclare les informations de langue et de culture pour un élément dans XML. Cette même signification de l’attribut persiste en XAML. Toutefois, certaines considérations supplémentaires s’appliquent.  
  
## Utilisation d'attributs XAML  
  
```  
<object xml:lang="rfc3066lang" />  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Chaîne dérivée de la norme [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) qui identifie une langue ou une langue\-région. Dans le dernier cas, la langue et la région sont séparées par un tiret. Pour plus d’informations sur les valeurs et le format, consultez <xref:System.Windows.Markup.XmlLanguage>.|  
  
## Notes  
 La définition de l’attribut `xml:lang` en [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] est dérivée de `xml:lang`, défini comme un « attribut spécial » par le [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] pour [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Les informations de langue et de culture peuvent être traitées de différentes façons par les éléments, selon leurs implémentations. Toutefois, il n’existe aucun traitement [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] par défaut de l’attribut `xml:lang`.  
  
 La valeur par défaut de l’attribut `xml:lang` est une chaîne vide au niveau de l’attribut.  
  
 Les effets et la valeur de l’attribut `xml:lang` sont généralement transmis aux éléments enfants, quand ils sont interprétés par des systèmes qui agissent sur les valeurs `xml:lang`.  
  
 Lorsqu’elle est interprétée par les writers XAML des services XAML du .NET Framework, une valeur `xml:lang` peut créer des objets <xref:System.Windows.Markup.XmlLanguage> ou <xref:System.Globalization.CultureInfo> dans la représentation d’objet sous\-jacente. Toutefois, ce comportement varie selon que la valeur spécifiée pour `xml:lang` est ou non une construction valide pour ces classes.  
  
 Les infrastructures peuvent créer des associations entre les propriétés définies par l’infrastructure et la signification de `xml:lang` dans XML en appliquant <xref:System.Windows.Markup.XmlLangPropertyAttribute> à la propriété.  
  
## Nœuds d’utilisation WPF  
 Pour les éléments qui sont des classes dérivées de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, vous pouvez utiliser la propriété de dépendance <xref:System.Windows.FrameworkElement.Language%2A> équivalente à la place de l’attribut `xml:lang`. Par défaut, la propriété <xref:System.Windows.FrameworkElement.Language%2A> utilise « en\-US » si elle n’est pas définie autrement via la propriété ou via le traitement de l’attribut `xml:lang`.  
  
## Voir aussi  
 [Globalisation pour WPF](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md)