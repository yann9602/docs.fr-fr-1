---
title: "class (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "class_CSharpKeyword"
  - "class"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "class (mot clé C#)"
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# class (r&#233;f&#233;rence C#)
Les classes sont déclarées à l'aide du mot clé `class`, comme illustré dans l'exemple suivant :  
  
```  
  
      class TestClass  
{  
    // Methods, properties, fields, events, delegates   
    // and nested classes go here.  
}  
```  
  
## Notes  
 Seul l'héritage unique en c.  Cela signifie qu'une classe ne peut hériter de l'implémentation que d'une seule classe de base.  En revanche, une classe peut implémenter plusieurs interfaces.  Le tableau suivant comporte des exemples d'héritage de classe et d'implémentation d'interface.  
  
|Héritage|Exemple|  
|--------------|-------------|  
|Aucun|`class ClassA { }`|  
|Single|`class DerivedClass: BaseClass { }`|  
|Aucun, implémente deux interfaces|`class ImplClass: IFace1, IFace2 { }`|  
|Unique, implémente une seule interface|`class ImplDerivedClass: BaseClass, IFace1 { }`|  
  
 Les classes que vous déclarez directement dans un espace de noms, non imbriquées dans d'autres classes, peuvent être [public](../../../csharp/language-reference/keywords/public.md) ou [interne](../../../csharp/language-reference/keywords/internal.md).  Les classes sont `internal` par défaut.  
  
 Les membres de classe, y compris les classes imbriquées, peuvent être [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protégé](../../../csharp/language-reference/keywords/protected.md), [interne](../../../csharp/language-reference/keywords/internal.md), ou [privé](../../../csharp/language-reference/keywords/private.md).  Les membres sont [privé](../../../csharp/language-reference/keywords/private.md) par défaut.  
  
 Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Vous pouvez déclarer les classes génériques ayant des paramètres de type.  Pour plus d'informations, consultez l' [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md).  
  
 Une classe peut contenir les déclarations des membres suivants :  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Indexeurs](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Événements](../../../csharp/programming-guide/events/index.md)  
  
-   [Délégués](../../../csharp/programming-guide/delegates/index.md)  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [Structures](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
## Exemple  
 L'exemple suivant explique comment déclarer des champs, constructeurs et méthodes de classe.  Il illustre aussi l'instanciation d'un objet et l'impression des données d'une instance.  Dans cet exemple, deux classes sont déclarées. La première classe, `Child`, contient deux champs privés \(`name` et `age`\) et deux méthodes publiques.  La deuxième classe, `StringTest`, est utilisée pour contenir `Main`.  
  
 [!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]  
  
## Commentaires  
 Notez que, dans l'exemple qui précède, les champs privés \(`name` et `age`\) ne sont accessibles que par le biais des méthodes publiques de la classe `Child`.  Par exemple, vous ne pouvez pas imprimer le nom de l'enfant, à partir de la méthode `Main`, en utilisant une instruction de ce type :  
  
```  
Console.Write(child1.name);   // Error  
```  
  
 L'accès aux membres privés de `Child` à partir de `Main` serait possible uniquement si `Main` était un membre de la classe.  
  
 Les types déclarés dans une classe sans modificateur d'accès ont comme valeur par défaut à `private`, les données membres dans cet exemple ont toujours `private` si le mot clé ont été supprimés.  
  
 Notez enfin que pour l'objet créé à l'aide du constructeur par défaut \(`child3`\), le champ  a été initialisé par défaut à la valeur zéro.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)