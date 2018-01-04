---
title: x:Arguments, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb1f5986a0d9f9eb69ade0228925ec06164cee4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xarguments-directive"></a>x:Arguments, directive
Arguments de construction de packages pour une déclaration d’élément objet constructeur personnalisé en XAML, ou pour une déclaration d’objet de fabrique (méthode)  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>Utilisation des éléments XAML (constructeur non défini par défaut)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Utilisation des éléments XAML (méthode de fabrique)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Un ou plusieurs éléments objet qui spécifient les arguments à passer à la méthode de constructeur ou de la fabrique par défaut de stockage.<br /><br /> Utilisation typique consiste à utiliser le texte d’initialisation dans les éléments de l’objet pour spécifier les valeurs de l’argument réel. Consultez la section Exemples.<br /><br /> L’ordre des éléments est significatif. Les types XAML dans l’ordre doivent correspondent aux types et ordre de type de la surcharge de méthode de constructeur ou de la fabrique de sauvegarde.|  
|`methodName`|Le nom de la méthode de fabrique qui doit traiter tous `x:Arguments` arguments.|  
  
## <a name="dependencies"></a>Dépendances  
 `x:FactoryMethod`peut modifier l’étendue et le comportement où `x:Arguments` s’applique.  
  
 Si aucun `x:FactoryMethod` est spécifié, `x:Arguments` s’applique pour alterner des signatures des constructeurs de sauvegarde (et non par défaut).  
  
 Si `x:FactoryMethod` est spécifié, `x:Arguments` s’applique à une surcharge de la méthode nommée.  
  
## <a name="remarks"></a>Notes  
 XAML 2006 peut prendre en charge l’initialisation par défaut dans le texte de l’initialisation. Toutefois, l’application pratique d’une technique de construction de texte d’initialisation est limitée. Texte d’initialisation est traité comme une chaîne de texte unique ; Par conséquent, il ajoute uniquement la fonctionnalité pour l’initialisation d’un paramètre unique, sauf si un convertisseur de type est défini pour le comportement de construction qui peut analyser des éléments personnalisés des informations et les délimiteurs personnalisés à partir de la chaîne. En outre, la chaîne de texte à la logique de l’objet est potentiellement convertisseur de type natif par défaut d’un analyseur XAML donnée pour la gestion des primitives de chaîne true.  
  
 Le `x:Arguments` l’utilisation de XAML n’est pas utilisation des éléments de propriété dans le sens classique, étant donné que le balisage de la directive ne référence pas de type de l’élément objet contenant. Il est plus apparenté à d’autres directives telles que `x:Code` où l’élément dénote une plage dans laquelle la balise doit être interprétée comme autre que la valeur par défaut pour le contenu enfant. Dans ce cas, le type de chaque élément d’objet XAML communique des informations sur les types d’arguments, qui sont utilisées par les analyseurs XAML pour déterminer la signature de méthode de fabrique constructeur spécifique un `x:Arguments` tente de référencer l’utilisation.  
  
 `x:Arguments`un élément de l’objet en cours de construction doit précéder toutes les autres éléments de propriété, le contenu, texte interne ou des chaînes d’initialisation de l’élément objet. Les éléments de l’objet au sein de `x:Arguments` peut inclure des attributs et des chaînes d’initialisation, comme autorisé par ce type XAML et sa méthode de constructeur ou de la fabrique de sauvegarde. Pour l’objet ou les arguments, vous pouvez spécifier les types XAML personnalisés ou les types XAML qui sont sinon en dehors de l’espace de noms XAML par défaut en référençant les mappages de préfixe établis.  
  
 Processeurs XAML utilisent les instructions suivantes pour déterminer la façon dont les arguments spécifiés dans `x:Arguments` doit être utilisé pour construire un objet. Si `x:FactoryMethod` est spécifié, les informations sont comparées à l’objet `x:FactoryMethod` (Notez que la valeur de `x:FactoryMethod` est le nom de méthode et la méthode nommée ont des surcharges. Si `x:FactoryMethod` n’est pas spécifié, les informations sont comparées à l’ensemble de toutes les surcharges de constructeur public de l’objet. Logique de traitement XAML puis compare le nombre de paramètres et sélectionne la surcharge avec l’arité correspondante. S’il existe plusieurs correspondances, le processeur XAML doit comparer les types des paramètres basés sur les types XAML d’éléments de l’objet fourni. Si plus d’une correspondance est trouvée, le comportement du processeur XAML est indéfini. Si un `x:FactoryMethod` est spécifié, mais la méthode ne peut pas être résolue, un processeur XAML doit lever une exception.  
  
 Une utilisation d’attributs XAML `<x:Arguments>string</x:Arguments>` est techniquement possible. Toutefois, cela ne fournit aucun fonctionnalités au-delà de ce qui peut être fait sinon via des convertisseurs de texte et le type de l’initialisation, et à l’aide de cette syntaxe n’est pas l’intention de la conception des fonctionnalités de méthode de fabrique XAML 2009.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre un constructeur par défaut de signature, puis l’utilisation de XAML de `x:Arguments` qui accède à cette signature.  
  
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
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 L’exemple suivant montre une signature de méthode de fabrique cible, puis l’utilisation de XAML de `x:Arguments` qui accède à cette signature.  
  
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
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
