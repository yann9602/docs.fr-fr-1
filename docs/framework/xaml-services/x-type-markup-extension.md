---
title: "x:Type Markup Extension | Microsoft Docs"
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
  - "x:TypeExtension"
  - "Type"
  - "x:Type"
  - "xType"
  - "TypeExtension"
helpviewer_keywords: 
  - "x:Type markup extension [XAML Services]"
  - "XAML [XAML Services], x:Type markup extension"
  - "XAML [XAML Services], TargetType attribute"
  - "TargetType attribute [XAML Services]"
  - "Type markup extension in XAML [XAML Services]"
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 27
---
# x:Type Markup Extension
Fournit l'objet CLR <xref:System.Type> qui est le type sous\-jacent pour un type XAML spécifié.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## Utilisation d'éléments objet XAML  
  
```  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`prefix`|Facultatif.  Préfixe qui mappe un espace de noms XAML non défini par défaut.  La spécification d'un préfixe n'est généralement pas nécessaire.  Consultez la section Notes.|  
|`typeNameValue`|Obligatoire.  Nom de type pouvant être résolu dans l'espace de noms XAML par défaut actuel ou préfixe mappé spécifié si `prefix` est fourni.|  
  
## Notes  
 L'extension de balisage `x:Type` a une fonction similaire à l'opérateur `typeof()` dans [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] ou à l'opérateur `GetType` dans [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].  
  
 L'extension de balisage `x:Type` fournit le comportement de la conversion de chaîne pour les propriétés qui prennent le type <xref:System.Type>.  L'entrée est un type XAML.  La relation entre le type XAML d'entrée et la sortie CLR <xref:System.Type> est que la sortie <xref:System.Type> est le <xref:System.Xaml.XamlType.UnderlyingType%2A> de l'entrée <xref:System.Xaml.XamlType>, après avoir recherché le <xref:System.Xaml.XamlType> nécessaire en fonction du contexte de schéma XAML et du service <xref:System.Windows.Markup.IXamlTypeResolver> fourni par le contexte.  
  
 Dans les services XAML .NET Framework, la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.Markup.TypeExtension>.  
  
 Dans les implémentations d'infrastructure spécifiques, certaines propriétés qui utilisent <xref:System.Type> comme une valeur sont capables d'accepter directement le nom du type \(valeur de chaîne du `Name` du type\).  Toutefois, l'implémentation d'un tel comportement est un scénario complexe.  Pour obtenir des exemples, consultez la section « Notes d'utilisation de WPF » ci\-après.  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  Le jeton de chaîne fourni après la chaîne d'identificateur `x:Type` est assigné en tant que valeur <xref:System.Windows.Markup.TypeExtension.TypeName%2A> de la classe d'extension <xref:System.Windows.Markup.TypeExtension> sous\-jacente.  Dans le contexte de schéma XAML par défaut pour les services XAML .NET Framework, qui est basé sur les types CLR, la valeur de cet attribut est le <xref:System.Reflection.MemberInfo.Name%2A> du type souhaité ou contient ce <xref:System.Reflection.MemberInfo.Name%2A>, précédé par un préfixe pour un mappage d'espace de noms XAML non défini par défaut.  
  
 L'extension de balisage `x:Type` peut être utilisée dans la syntaxe d'élément objet.  Dans ce cas, vous devez spécifier la valeur de la propriété <xref:System.Windows.Markup.TypeExtension.TypeName%2A> pour initialiser correctement l'extension.  
  
 L'extension de balisage `x:Type` peut également être utilisée comme attribut brut ; toutefois, cette utilisation n'est pas courante : propriété de l'objet `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## Remarques sur l'utilisation de WPF  
  
### Espace de noms XAML par défaut et mappage de types  
 L'espace de noms XAML par défaut pour la programmation WPF contient la plupart des types XAML dont vous avez besoin pour les scénarios XAML standard. Cela vous permet souvent d'éviter l'utilisation de préfixes lors du référencement de valeurs de types XAML.  Vous devrez peut\-être mapper un préfixe si vous référencez un type d'un assembly personnalisé, ou pour les types qui existent dans un assembly WPF mais qui sont dans un espace de noms CLR qui n'a pas été mappé à l'espace de noms XAML par défaut.  Pour plus d'informations sur les préfixes, les espaces de noms XAML et le mappage des espaces de noms CLR, consultez [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../ocs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### Propriétés de types prenant en charge Typename\-as\-String  
 WPF prend en charge des techniques permettant la spécification de la valeur de certaines propriétés de type <xref:System.Type> sans requérir une utilisation d'extension de balisage `x:Type`.  À la place, vous pouvez spécifier la valeur comme une chaîne qui nomme le type.  Les exemples de ceci sont <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=fullName> et <xref:System.Windows.Style.TargetType%2A?displayProperty=fullName>.  La prise en charge de ce comportement n'est pas fournie via des convertisseurs de type ou des extensions de balisage.  À la place, c'est un comportement de report implémenté via <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight prend en charge une convention similaire.  En fait, à l'heure actuelle, Silverlight ne prend pas en charge `{x:Type}` dans sa prise en charge de langage XAML, et n'accepte pas les utilisations de `{x:Type}` en dehors de certaines circonstances qui sont prévues pour prendre en charge la migration du XAML WPF\-Silverlight.  Par conséquent, le comportement Typename\-as\-String est intégré à toute évaluation de propriété native de Silverlight où un <xref:System.Type> est la valeur.  
  
## XAML 2009  
 XAML 2009 fournit un support supplémentaire pour les types génériques et modifie le comportement de fonctionnalité de `x:TypeArguments` et `x:Type` pour fournir ce support.  
  
-   `x:TypeArguments` et l'élément objet associé pour une instanciation d'objet générique peuvent être appliqués à des éléments autres que la racine.  Pour plus d'informations, consultez la section « XAML 2009 » de [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 prend en charge une syntaxe pour la spécification de la contrainte d'un type générique dans la balise.  Cela peut être utilisé par `x:TypeArguments`, par `x:Type` ou par les deux fonctionnalités ensemble.  
  
-   L'implémentation XAML WPF lors du traitement de XAML 2009 pour le chargement ajoute également cette fonction au comportement de conversion de type implicite pour les certaines propriétés d'infrastructure qui utilisent le type <xref:System.Type>.  
  
 Dans WPF, vous pouvez utiliser des fonctionnalités XAML 2009, mais uniquement pour XAML libre \(XAML pas compilé par balise\).  Le XAML compilé par balisage pour WPF et la forme de langage BAML de XAML ne prend actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
## Voir aussi  
 <xref:System.Windows.Style>   
 [Application d'un style et création de modèles](../../../ocs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../ocs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)