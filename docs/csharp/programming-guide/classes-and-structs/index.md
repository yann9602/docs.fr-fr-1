---
title: "Classes et structs (Guide de programmation C#)"
description: "Décrit l’utilisation des classes et des structures (structs) en C#."
keywords: "classes (C#), structs (C#), structures (structures) (C#), types référence (C#), types valeur (C#)"
ms.date: 2016-01-17
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: 48
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2076de96c58fb89813495cb59adacb8a0082d93c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="classes-and-structs-c-programming-guide"></a>Classes et structs (Guide de programmation C#)
Les classes et structs sont deux des constructions de base du système de type commun dans le .NET Framework. Chacun est en substance une structure de données qui encapsule un ensemble de données et de comportements constituant une unité logique. Les données et comportements sont les *membres* de la classe ou du struct, et ils incluent ses méthodes, propriétés, événements, etc., comme indiqué plus loin dans cette rubrique.  
  
 Une déclaration de classe ou de struct est comme un plan utilisé pour créer des instances ou des objets au moment de l'exécution. Si vous définissez une classe ou un struct nommé `Person`, `Person` est le nom du type. Si vous déclarez et initialisez une variable `p` de type `Person`, `p` est dit objet ou instance de `Person`. Plusieurs instances du même type `Person` peuvent être créées, et chaque instance peut avoir des valeurs différentes dans ses propriétés et champs.  
  
 Une classe est un type de référence. Lorsqu’un objet de la classe est créé, la variable à laquelle l’objet est affecté conserve uniquement une référence à cette mémoire. Lorsque la référence d’objet est affectée à une variable, la nouvelle variable fait référence à l’objet d’origine. Les modifications apportées à une variable sont répercutées sur l’autre variable, car toutes deux font référence aux mêmes données.  
  
 Un struct est un type valeur. Lorsqu'un struct est créé, la variable à laquelle le struct est assigné contient les données réelles du struct. Lorsque le struct est affecté à une nouvelle variable, il est copié. La nouvelle variable et la variable d’origine contiennent par conséquent deux copies distinctes des mêmes données. Les modifications apportées à une copie n’affectent pas l’autre copie.  
  
 En général, les classes sont utilisées pour modéliser des comportements plus complexes, ou des données destinées à être modifiées après la création d’un objet de classe. Les structs conviennent mieux aux petites structures de données contenant principalement des données qui ne sont pas censées être modifiées après que la structure a été créé.  
  
 Pour plus d’informations, consultez [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md), [Objets](../../../csharp/programming-guide/classes-and-structs/objects.md) et [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `CustomClass` dans l’espace de noms `ProgrammingGuide` a trois membres : un constructeur d’instance, une propriété nommée `Number` et une méthode nommée `Multiply`. La méthode `Main` de la classe `Program` crée une instance (objet) de `CustomClass`, et la méthode et la propriété de l’objet sont accessibles avec la notation par points.
  
 [!code-cs[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Encapsulation  
 *L’encapsulation* est parfois considérée comme le premier pilier ou principe de la programmation orientée objet. D'après le principe d'encapsulation, une classe ou un struct peut spécifier le degré d'accessibilité de chacun de ses membres au code situé en dehors de la classe ou du struct. Les méthodes et variables qui ne sont pas destinées à être utilisées d’en dehors de la classe ou de l’assembly peuvent être masquées afin de limiter le risque d’erreurs ou de code malveillant exploitant une faille de sécurité.  
  
 Pour plus d’informations sur les classes, consultez les pages [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) et [Objets](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Membres  
 Tous les champs, méthodes, constantes, propriétés et événements doivent être déclarés dans un type ; ils sont appelés *membres* du type. En C#, il n’existe aucune variable ou méthode globale, à la différence d’autres langages. Même le point d’entrée d’un programme, la méthode `Main`, doit être déclaré dans une classe ou un struct. La liste suivante inclut tous les types de membres qui peuvent être déclarés dans une classe ou un struct.  
  
-   [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Événements](../../../csharp/programming-guide/events/index.md)  
  
-   [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Indexeurs](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Accessibilité  
 Certaines méthodes et propriétés sont censées être appelées ou accessibles par le code qui se trouve à l’extérieur de votre classe ou de votre struct, connu sous le terme de *code client*. D’autres méthodes et propriétés peuvent être uniquement utilisables dans la classe ou le struct proprement dits. Il est important de limiter l’accessibilité de votre code afin que seul le code client prévu puisse y accéder. Vous pouvez spécifier l’accessibilité de vos types et de leurs membres vis-à-vis du code client à l’aide des modificateurs d’accès [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), `protected internal` et [private](../../../csharp/language-reference/keywords/private.md). L’accessibilité par défaut est `private`. Pour plus d’informations, consultez la page [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Héritage  
 Les classes (mais pas les structs) prennent en charge le concept d'héritage. Une classe qui dérive d’une autre classe (la *classe de base*) contient automatiquement tous les membres publics, protégés et internes de la classe de base, sauf ses constructeurs et finaliseurs. Pour plus d’informations, consultez les pages [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md) et [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Les classes peuvent être déclarées comme [abstraites](../../../csharp/language-reference/keywords/abstract.md), ce qui signifie qu’une ou plusieurs de leurs méthodes n’ont aucune implémentation. Bien que les classes abstraites ne puissent pas être instanciées directement, elles peuvent servir de classes de base à d’autres classes qui fournissent l’implémentation manquante. Les classes peuvent également être déclarées comme [scellées](../../../csharp/language-reference/keywords/sealed.md) pour empêcher d’autres classes d’hériter d’elles. Pour plus d’informations, consultez la page [Classes abstraites et scellées et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Interfaces  
 Les classes et les structs peuvent hériter de plusieurs interfaces. Pour un type, hériter d’une interface signifie implémenter toutes les méthodes définies dans l’interface. Pour plus d’informations, consultez la page [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Types génériques  
 Les classes et structs peuvent être définis avec un ou plusieurs paramètres de type. Le code client fournit le type lorsqu’il crée une instance du type. Par exemple, la classe <xref:System.Collections.Generic.List%601> de l’espace de noms <xref:System.Collections.Generic> est définie avec un seul paramètre de type. Le code client crée une instance d’une `List<string>` ou d’une `List<int>` pour spécifier le type que contiendra la liste. Pour plus d’informations, consultez la page [Génériques](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Types statiques  
 Les classes (mais pas les structs) peuvent être déclarées comme [statiques](../../../csharp/language-reference/keywords/static.md). Une classe statique ne peut contenir que des membres statiques et ne peut pas être instanciée avec le mot clé new. Une copie de la classe est chargée en mémoire au chargement du programme, et ses membres sont accessibles par le biais du nom de la classe. Les classes et les structs peuvent contenir des membres statiques. Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Types imbriqués  
 Une classe ou un struct peut être imbriqué dans une autre classe ou un autre struct. Pour plus d’informations, consultez [Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Types partiels  
 Vous pouvez définir une partie d'une classe, d'un struct ou d'une méthode dans un fichier de code et une autre partie dans un fichier de code séparé. Pour plus d’informations, consultez la page [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Initialiseurs d'objets  
 Vous pouvez instancier et initialiser des objets de classe et de struct, ainsi que des collections d'objets, sans appeler explicitement leur constructeur. Pour plus d’informations, consultez la page [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Types anonymes  
 Dans les situations où il n’est pas pratique ou nécessaire de créer une classe nommée, par exemple pour remplir une liste avec des structures de données qu’il n’est pas nécessaire de conserver ou de transmettre à une autre méthode, on utilise des types anonymes. Pour plus d’informations, consultez la page [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>méthodes d’extension.  
 Vous pouvez « étendre » une classe sans créer de classe dérivée en créant un type séparé dont les méthodes peuvent être appelées comme si elles appartenaient au type d’origine. Pour plus d’informations, consultez la page [Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Variables locales implicitement typées  
 Dans une méthode de classe ou de struct, vous pouvez utiliser le type implicite pour indiquer au compilateur de déterminer le type approprié au moment de la compilation. Pour plus d’informations, consultez la page [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)

