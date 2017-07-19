---
title: "x:TypeArguments Directive | Microsoft Docs"
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
  - "x:TypeArguments"
  - "xTypeArguments"
  - "TypeArguments"
helpviewer_keywords: 
  - "x:TypeArguments attribute [XAML Services]"
  - "TypeArguments attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:TypeArguments attribute"
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: 18
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 18
---
# x:TypeArguments Directive
Passe les arguments de type contraignant d'un générique au constructeur du type générique.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:TypeArguments="typeString" .../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`object`|Déclaration d'élément objet d'un type XAML, qui est stockée par un type générique CLR.  Si `object` fait référence à un type XAML qui n'est pas d'espace de noms XAML par défaut, `object` nécessite un préfixe pour indiquer l'espace de noms XAML où `object` existe.|  
|`typeString`|Chaîne qui déclare un ou plusieurs noms de type XAML sous forme de chaînes, ce qui fournit les arguments de type pour le type CLR générique.  Consultez les Remarques pour obtenir des remarques de syntaxe supplémentaires.|  
  
## Notes  
 Dans la plupart des cas, les types XAML qui sont utilisés comme élément d'information dans la chaîne `typeString` sont préfixés.  Les types classiques de contraintes génériques CLR \(par exemple, <xref:System.Int32> et <xref:System.String>\) sont extraites des bibliothèques de classes de base CLR.  Ces bibliothèques ne sont pas mappées aux espaces de noms XAML spécifiques à l'infrastructure par défaut typiques, et donc requièrent un mappage de préfixe pour l'utilisation de XAML.  
  
 Vous pouvez spécifier plusieurs noms de types XAML à l'aide d'une virgule de délimitation.  
  
 Si les contraintes génériques elles\-mêmes utilisent des types génériques, les arguments de type de contrainte imbriqué peuvent être contenus par des parenthèses \(\).  
  
 Notez que cette définition de `x:TypeArguments` est spécifique aux services XAML .NET Framework et à l'utilisation du stockage CLR.  Une définition relative au langage se trouve dans [\[MS\-XAML\] Section 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## Exemple d'utilisation  
 Pour ces exemples, supposez que les définitions d'espaces de noms XAML suivantes sont déclarées :  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### List\<String\>  
 `<scg:List x:TypeArguments="sys:String" ...>` instancie un nouveau <xref:System.Collections.Generic.List%601> avec un argument de type <xref:System.String>.  
  
### Dictionary\<String,String\>  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instancie un nouveau <xref:System.Collections.Generic.Dictionary%602> avec deux arguments de type <xref:System.String>.  
  
### Queue\<KeyValuePair\<String,String\>\>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instancie un nouveau <xref:System.Collections.Generic.Queue%601> qui a une contrainte de <xref:System.Collections.Generic.KeyValuePair%602>, avec les arguments de type de contrainte interne <xref:System.String> et <xref:System.String>.  
  
## XAML 2006 et utilisations XAML génériques WPF  
 Pour une utilisation XAML 2006, et un XAML utilisé pour les applications WPF, les restrictions suivantes existent pour `x:TypeArguments` et les utilisations de type générique de XAML en général :  
  
-   Seul l'élément racine d'un fichier XAML peut prendre en charge une utilisation XAML générique qui référence un type générique.  
  
-   L'élément racine doit être mappé à un type générique avec au moins un argument de type.  C'est le cas notamment de <xref:System.Windows.Navigation.PageFunction%601>.  Le principal scénario de prise en charge de l'utilisation du XAML générique dans WPF sont les fonctions de page.  
  
-   L'élément objet de l'élément racine XAML pour le type générique doit également déclarer une classe partielle à l'aide de `x:Class`.  Ceci est vrai, même lors de la définition d'une action de génération WPF  
  
-   `x:TypeArguments` ne peut pas référencer de contraintes génériques imbriquées.  
  
## XAML 2009 ou XAML 2006 sans dépendance WPF 3.0 or WPF 3.5  
 Dans les services XAML de .NET Framework pour XAML 2006 ou XAML 2009, les restrictions WPF sur l'utilisation générique de XAML sont assouplies.  Vous pouvez instancier un élément objet générique à toute position dans le balisage XAML que le système de type de stockage et le modèle objet peuvent prendre en charge.  
  
 Si vous utilisez le langage XAML 2009 au lieu du mappage des types de base CLR pour obtenir des types XAML pour les primitives de langage commun, vous pouvez utiliser les [types intégrés des primitives de langage XAML commun](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) en tant qu'éléments d'informations dans `typeString`.  Par exemple, vous pouvez déclarer les éléments suivants \(les mappages de préfixes ne sont pas indiqués, mais x est l'espace de noms XAML du langage XAML 2009\) :  
  
```  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 Dans WPF et lorsque vous ciblez [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser les fonctionnalités de XAML 2009 avec `x:TypeArguments` mais uniquement pour le XAML libre \(XAML qui n'est pas compilé par balisage\).  Le XAML compilé par balisage pour WPF et la forme de langage BAML de XAML ne prend actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  Si vous avez besoin de compiler le XAML par balisage, vous devez fonctionner selon les restrictions notées dans la section « Utilisations de XAML 2006 et de XAML WPF générique ».  
  
## Voir aussi  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [Types intégrés pour les primitives associées au langage XAML courant](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)   
 [Generics in XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)