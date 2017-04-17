---
title: "x:Arguments Directive | Microsoft Docs"
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
  - "x:Arguments directive [XAML Services]"
  - "Arguments directive in XAML [XAML Services]"
  - "XAML [XAML Services], x:Arguments directive"
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: 12
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 12
---
# x:Arguments Directive
Arguments de génération de packages pour une déclaration d'élément objet non définie par défaut de constructeur en XAML, ou pour une déclaration d'objet méthode de fabrique.  
  
## Utilisation de l'élément XAML \(constructeur non défini par défaut\)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## Utilisation de l'élément XAML \(méthode de fabrique\)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Un ou plusieurs éléments objet qui spécifient les arguments à passer au constructeur de stockage ou à la méthode de fabrique non par défaut.<br /><br /> Une utilisation classique consiste à utiliser le texte d'initialisation dans les éléments objet pour spécifier les valeurs d'argument réelles.  Consultez la section des exemples.<br /><br /> L'ordre des éléments du tableau a de l'importance.  Les types XAML dans l'ordre doivent correspondre aux types et à l'ordre de type de la surcharge de la méthode de stockage de constructeur\/fabrique.|  
|`methodName`|Le nom de la méthode d'usine qui doit traiter tous les arguments `x:Arguments`.|  
  
## Dépendances  
 `x:FactoryMethod` peut modifier la portée et le comportement lorsque `x:Arguments` est applicable.  
  
 Si aucun `x:FactoryMethod` n'est spécifié, `x:Arguments` s'applique pour alterner des signatures \(non définies par défaut\) des constructeurs de stockage.  
  
 Si `x:FactoryMethod` est spécifié, `x:Arguments` s'applique à une surcharge de la méthode nommée.  
  
## Notes  
 XAML 2006 peut prendre en charge l'initialisation non définie par défaut par le biais du texte d'initialisation.  Toutefois, l'application pratique d'une technique de construction du texte de l'initialisation est limitée.  Le texte d'initialisation est traité comme chaîne de texte unique ; par conséquent, il ajoute uniquement la capacité pour une initialisation de paramètre à moins qu'un convertisseur de type ne soit défini pour le comportement de génération qui peut analyser les éléments personnalisés des informations et les délimiteurs personnalisés de la chaîne.  En outre, la chaîne de texte à la logique d'objet est potentiellement un convertisseur de type natif par défaut d'un analyseur XAML pour administrer les primitives autres qu'une chaîne true.  
  
 L'utilisation XAML `x:Arguments` n'est pas une utilisation de l'élément de propriété au sens strict, car la balise de la directrice ne fait pas référence au type de l'élément objet contenant.  C'est plus apparenté à d'autres directives telles que `x:Code` où l'élément dénote une plage dans laquelle la balise doit être interprétée comme autre que la valeur par défaut pour le contenu enfant.  Dans ce cas, le type XAML de chaque élément d'objet communique les informations sur les types d'argument, qui sont utilisées par les analyseurs XAML pour déterminer quelle signature de fabrique de constructeur spécifiée fait l'objet d'une tentative de référencement par `x:Arguments`.  
  
 `x:Arguments` pour un élément objet en cours de génération doit précéder tous les autres éléments de propriété, contenus texte interne ou chaînes d'initialisation de l'élément objet.  Les éléments objet dans `x:Arguments` peuvent inclure des attributs et des chaînes d'initialisation, comme autorisé par ce type XAML et son constructeur de stockage ou méthode d'usine.  Pour l'objet ou les arguments, vous pouvez spécifier les types XAML personnalisés ou les types XAML qui sont sinon en dehors de l'espace de noms XAML par défaut en référençant les mappages de préfixe établis.  
  
 Les processeurs XAML utilisent les instructions suivantes pour déterminer comment les arguments spécifiés dans `x:Arguments` doivent être utilisés pour construire un objet.  Si `x:FactoryMethod` est spécifié, les informations sont comparées à `x:FactoryMethod` spécifié \(notez que la valeur de `x:FactoryMethod` est le nom de la méthode, et la méthode nommée peut avoir des surcharges.  Si `x:FactoryMethod` n'est pas spécifié, les informations sont comparées à l'ensemble de toutes les surcharges de constructeur public de l'objet.  La logique de traitement XAML compare ensuite le nombre de paramètres et choisit la surcharge avec l'arité correspondante.  S'il existe plusieurs correspondances, le processeur XAML doit comparer les types des paramètres en fonction des types XAML des éléments d'objet fournis.  S'il y a encore plusieurs correspondances, le comportement du processeur XAML est indéfini.  Si `x:FactoryMethod` est spécifié, mais que la méthode ne peut pas être résolue, un processeur XAML doit lever une exception.  
  
 Une utilisation `<x:Arguments>string</x:Arguments>` d'attribut XAML est techniquement possible.  Toutefois, cela ne vous permet d'effectuer aucune opération au delà de ce qui peut être fait sinon via le texte d'initialisation et les convertisseurs de type, et l'utilisation de cette syntaxe n'est pas l'intention de création de fonctionnalités de méthode de fabrique XAML 2009.  
  
## Exemples  
 L'exemple suivant montre une signature de constructeur non définie par défaut, puis l'utilisation XAML de `x:Arguments` qui accède à cette signature.  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 L'exemple suivant montre une signature de méthode d'usine cible, puis l'utilisation XAML de `x:Arguments` qui accède à cette signature.  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## Voir aussi  
 [Defining Custom Types for Use with .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)