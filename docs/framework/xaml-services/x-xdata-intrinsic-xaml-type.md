---
title: "x:XData Intrinsic XAML Type | Microsoft Docs"
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
  - "x:XData"
  - "XData"
  - "xXData"
helpviewer_keywords: 
  - "XAML [XAML Services], x:XData directive element"
  - "XData in XAML [XAML Services]"
  - "x:XData XAML directive element [XAML Services]"
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: 17
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 17
---
# x:XData Intrinsic XAML Type
Active le placement des îlots de données XML dans une production XAML.  Les éléments XML `x:XData` ne doivent pas être traités par les processeurs XAML comme faisant partie de l'espace de noms XAML par défaut actif ou tout autre espace de noms XAML.  `x:XData` peut contenir du code XML bien formé arbitraire.  
  
## Utilisation d'éléments objet XAML  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`elementDataRoot`|Élément racine unique de l'îlot de données incorporé.  Pour la plupart des consommateurs éventuels, un XML qui n'a pas de racine unique est considéré comme non valide.  En particulier, une racine unique est requise si `x:XData` est attendu comme source de données XML pour WPF ou bien d'autres technologies qui utilisent des sources XML pour la liaison de données.|  
|`[elementData]`|Facultatif.  Le XML représentant les données XML.  Tout nombre d'éléments peut être contenu comme données d'élément et les éléments imbriqués peuvent être contenus dans d'autres éléments ; cependant, les règles générales de XML s'appliquent.|  
  
## Notes  
 Les éléments XML d'un objet `x:XData` peuvent déclarer de nouveau tous les espaces de noms et préfixes possibles contenant XMLDOM dans leurs données.  
  
 Un accès par programme à des données XML et au `x:XData` type XAML intrinsèque est possible dans les services XAML .NET Framework via la classe <xref:System.Windows.Markup.XData>.  
  
## Remarques sur l'utilisation de WPF  
 L'objet `x:XData` est utilisé principalement comme objet enfant d'un <xref:System.Windows.Data.XmlDataProvider>, ou bien comme objet enfant de la propriété <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=fullName> \(en XAML, cela est exprimé en général dans la syntaxe des éléments de propriété\).  
  
 En règle générale, les données doivent redéfinir l'espace de noms XML de base dans l'îlot de données en tant que nouvel espace de noms XML par défaut \(ayant pour valeur une chaîne vide\).  C'est plus facile pour les îlots de données simples car les expressions <xref:System.Windows.Data.Binding.XPath%2A> utilisées pour référencer et lier les données peuvent éviter l'inclusion de préfixes.  Les îlots de données plus complexes peuvent choisir de définir plusieurs préfixes pour les données et d'utiliser un préfixe spécifique pour l'espace de noms XML à la racine.  Dans ce cas, toutes les références d'expression <xref:System.Windows.Data.Binding.XPath%2A> devront inclure le préfixe mappé par espace de noms approprié.  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Techniquement parlant, `x:XData` peut être utilisé comme contenu de toute propriété de type <xref:System.Xml.Serialization.IXmlSerializable>.  Cependant <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=fullName> est toutefois la seule implémentation apparente.  
  
## Voir aussi  
 <xref:System.Windows.Data.XmlDataProvider>   
 [Vue d'ensemble de la liaison de données](../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Binding, extension de balisage](../../../docs/framework/wpf/advanced/binding-markup-extension.md)