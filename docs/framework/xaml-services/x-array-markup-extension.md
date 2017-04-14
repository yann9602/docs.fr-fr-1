---
title: "x:Array Markup Extension | Microsoft Docs"
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
  - "x:Array"
  - "xArray"
helpviewer_keywords: 
  - "x:Array [XAML Services]"
  - "XAML [XAML Services], x:Array markup extension"
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Array Markup Extension
Fournit une prise en charge générale pour les tableaux d'objets en XAML, via une extension de balisage.  Cela correspond au type XAML `x:ArrayExtension` en \[MS\-XAML\].  
  
## Utilisation d'éléments objet XAML  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`typeName`|Nom du type contenu dans votre `x:Array`.  `typeName` peut être \(et est souvent\) préfixé  pour un espace de noms XAML qui contient les définitions de type XAML.|  
|`arrayContents`|Contenu d'éléments assigné à la propriété `ArrayExtension.Items` intrinsèque.  En général, ces éléments sont spécifiés comme un ou plusieurs éléments objet contenus dans les balises d'ouverture et de fermeture `x:Array`.  Les objets spécifiés ici sont supposés être assignables au type XAML spécifié dans `typeName`.|  
  
## Notes  
 `Type` est un attribut requis pour tous les éléments objet `x:Array`.  Une valeur de paramètre `Type` n'a pas besoin d'utiliser une extension de balisage `x:Type`; le nom court du type est un type XAML qui peut être spécifié sous forme de chaîne.  
  
 Dans l'implémentation des services XAML .NET Framework, les relations entre le type XAML d'entrée et le CLR <xref:System.Type> de sortie du tableau créé sont influencées par le contexte de service pour des extensions de balisage.  La sortie <xref:System.Type> est la <xref:System.Xaml.XamlType.UnderlyingType%2A> du type XAML d'entrée,  après avoir recherché le  nécessaire <xref:System.Xaml.XamlType> en fonction du contexte de schéma XAML et du service <xref:System.Windows.Markup.IXamlTypeResolver> fourni par le contexte.  
  
 Lorsqu'il est traité, le contenu d'un tableau est assigné à la propriété intrinsèque `ArrayExtension.Items`.  Dans l'implémentation <xref:System.Windows.Markup.ArrayExtension>, cela est représenté par <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=fullName>.  
  
 Dans l'implémentation des services XAML .NET Framework, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.ArrayExtension>.  <xref:System.Windows.Markup.ArrayExtension> n'est pas sealed et pourrait être utilisée comme base pour une implémentation d'extension de balisage pour un type de tableau personnalisé.  
  
 `x:Array` est davantage conçu pour l'extensibilité de langage générale en XAML.  Mais `x:Array` peut également être utile pour spécifier les valeurs XAML de certaines propriétés qui utilise des collections XAML comme contenu de propriété structuré.  Par exemple, vous pourriez spécifier le contenu d'une propriété <xref:System.Collections.IEnumerable> avec une utilisation `x:Array`.  
  
 `x:Array` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  `x:Array` est partiellement une exception à cette règle, parce qu'au lieu de fournir un traitement différent de la valeur d'attribut, `x:Array` fournit un autre traitement de son contenu de texte interne.  Ce comportement permet aux types qui peuvent ne pas être pris en charge par un modèle de contenu existant d'être regroupés dans un tableau et référencés ultérieurement en code\-behind en accédant au tableau nommé ; vous pouvez appeler les méthodes <xref:System.Array> pour obtenir les éléments de tableau individuels.  
  
 En XAML, toutes les extensions de balisage utilisent les accolades \({,}`)` dans leur syntaxe d'attributs, convention selon laquelle un processeur XAML reconnaît qu'une extension de balisage doit traiter l'attribut.  Pour plus d'informations sur les extensions de balisage en général, consultez [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Dans XAML 2009, `x:Array` est défini comme une primitive de langage plutôt que comme une extension de balisage.  Pour plus d'informations, consultez [Built\-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).  
  
## Remarques sur l'utilisation de WPF  
 En général, les éléments objet qui remplissent un `x:Array` ne sont pas des éléments qui existent dans l'espace de noms XAML [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] et requièrent un mappage de préfixe à un espace de noms XAML non défini par défaut.  
  
 L'exemple suivant correspond à un tableau simple de deux chaînes, avec le préfixe `sys` \(et `x`\) défini au niveau du tableau :  
  
 \[xaml\]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Pour les types personnalisés utilisés comme éléments de tableau, la classe doit également prendre en charge les spécifications instanciées en XAML comme éléments objet.  Pour plus d'informations, consultez [XAML et classes personnalisées pour WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## Voir aussi  
 [Extensions de balisage et XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)