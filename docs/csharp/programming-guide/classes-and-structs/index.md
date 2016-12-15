---
title: "Classes et structs (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, classes"
  - "langage C#, objets"
  - "langage C#, structs"
  - "classes (C#), vue d'ensemble"
  - "objets (C#)"
  - "structures (C#), à propos des structs"
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: 48
caps.handback.revision: 48
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Classes et structs (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les classes et structs sont deux des constructions de base du système de type commun dans le .NET Framework.  Chacun est essentiellement une structure de données qui encapsule un groupe de données et des comportements qui ensemble constituent une unité logique.  Les données et comportements sont les *membres* de la classe ou du struct, et ils incluent ses méthodes, propriétés, événements, et ainsi de suite, comme répertorié ultérieurement dans cette rubrique.  
  
 Une déclaration de classe ou de struct est comme un plan utilisé pour créer des instances ou des objets au moment de l'exécution.  Si vous définissez une classe ou un struct nommé `Person`, `Person` est le nom du type.  Si vous déclarez et initialisez une variable `p` de type `Person`, on dit que `p` est un objet ou une instance de `Person`.  Vous pouvez créer plusieurs instances du même type `Person` et chaque instance peut avoir des valeurs différentes dans ses propriétés et champs.  
  
 Une classe est un type référence.  Lorsqu'un objet de la classe est créé, la variable à laquelle l'objet est assigné contient uniquement une référence à cette mémoire.  Lorsque la référence d'objet est assignée à une nouvelle variable, la nouvelle variable fait référence à l'objet d'origine.  Les modifications effectuées par le biais d'une variable sont répercutées dans l'autre variable car toutes deux font référence aux mêmes données.  
  
 Un struct est un type valeur.  Lorsqu'un struct est créé, la variable à laquelle le struct est assigné contient les données réelles du struct.  Lorsque le struct est assigné à une nouvelle variable, il est copié.  La nouvelle variable et la variable d'origine contiennent par conséquent deux copies distinctes des mêmes données.  Les modifications apportées à une copie n'affectent pas l'autre copie.  
  
 En général, les classes sont utilisées pour modeler un comportement plus complexe ou des données censées être modifiées après la création d'un objet de classe.  Les structs conviennent mieux aux petites structures de données contenant principalement des données qui ne sont pas censées être modifiées après la création du struct.  
  
 Pour plus d'informations, consultez [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md), [Objets](../../../csharp/programming-guide/classes-and-structs/objects.md) et [Structures](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## Exemple  
 Dans l'exemple suivant, `MyCustomClass` est défini avec trois membres au niveau supérieur de l'espace de noms `ProgrammingGuide`.  Une instance \(objet\) de `MyCustomClass` est créée dans la méthode `Main` dans la classe `Program`, et les méthodes et propriétés de l'objet sont accessibles à l'aide de la notation par point.  
  
 [!code-cs[csProgGuideObjects#88](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_1.cs)]  
  
## Encapsulation  
 L'*encapsulation* est parfois connu sous le nom de premier pilier ou principe de la programmation orientée objet.  D'après le principe d'encapsulation, une classe ou un struct peut spécifier le degré d'accessibilité de chacun de ses membres au code situé en dehors de la classe ou du struct.  Les méthodes et variables qui ne sont pas censées être utilisées depuis l'extérieur de la classe ou de l'assembly peuvent être masquées afin de limiter le risque d'erreurs de codage ou d'utilisation malveillante.  
  
 Pour plus d'informations sur les classes, consultez [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) et [Objets](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### Membres  
 Tous les champs, méthodes, constantes, propriétés et événements doivent être déclarés dans un type ; ils portent le nom de *membres* du type.  En C\#, il n'y a pas de variables ou méthodes globales comme dans certains autres langages.  Même le point d'entrée d'un programme, la méthode `Main`, doit être déclaré dans une classe ou un struct.  La liste suivante inclut tous les types de membres qui peuvent être déclarés dans une classe ou un struct.  
  
-   [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Événements](../../../csharp/programming-guide/events/index.md)  
  
-   [Indexeurs](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### Accessibilité  
 Certaines méthodes et propriétés sont censées être appelées ou accédées à partir de code à l'extérieur de votre classe ou struct, connu sous le terme de *code client*.  D'autres méthodes et propriétés peuvent être destinées uniquement à une utilisation dans la classe ou le struct lui\-même.  Il est important de limiter l'accessibilité de votre code afin que seul le code client prévu puisse y accéder.  Vous pouvez spécifier le degré d'accessibilité de vos types et de leurs membres au code client en utilisant les modificateurs d'accès [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), `protected internal` et [private](../../../csharp/language-reference/keywords/private.md).  L'accessibilité  par défaut est `private`.  Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### Héritage  
 Les classes \(mais pas les structs\) prennent en charge le concept d'héritage.  Une classe qui dérive d'une autre classe \(la *classe de base*\) contient automatiquement tous les membres publics, protégés et internes de la classe de base, sauf ses constructeurs et destructeurs.  Pour plus d'informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md) et [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Les classes peuvent être déclarées comme [abstraites](../../../csharp/language-reference/keywords/abstract.md), ce qui signifie qu'une ou plusieurs de leurs méthodes n'a aucune implémentation.  Bien que les classes abstraites ne puissent pas être instanciées directement, elles peuvent servir de classes de base à d'autres classes qui fournissent l'implémentation manquante.  Les classes peuvent également être déclarées comme [sealed](../../../csharp/language-reference/keywords/sealed.md) pour empêcher d'autres classes d'hériter d'elles.  Pour plus d'informations, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### Interfaces  
 Les classes et structs peuvent hériter de plusieurs interfaces.  Hériter de l'interface signifie que le type implémente toutes les méthodes définies dans cette interface.  Pour plus d'informations, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
### Types génériques  
 Les classes et structs peuvent être définis avec un ou plusieurs paramètres de type.  Le code client fournit le type lorsqu'il crée une instance du type.  Par exemple, la classe <xref:System.Collections.Generic.List%601> dans l'espace de noms <xref:System.Collections.Generic> est définie avec un paramètre de type.  Le code client crée une instance d'un `List<string>` ou `List<int>` pour spécifier le type que la liste contiendra.  Pour plus d'informations, consultez [Génériques](../../../csharp/programming-guide/generics/index.md).  
  
### Types statiques  
 Les classes \(mais pas les structs\) peuvent être déclarées comme [statiques](../../../csharp/language-reference/keywords/static.md).  Une classe statique peut contenir des membres statiques uniquement et ne peut pas être instanciée avec le mot clé New.  Une copie de la classe est chargée dans la mémoire lorsque le programme charge, et ses membres sont accessibles via le nom de classe.  Les classes et les structs peuvent contenir des membres statiques.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### Types imbriqués  
 Une classe ou un struct peut être imbriqué dans une autre classe ou struct.  Pour plus d'informations, consultez [Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### Types partiels  
 Vous pouvez définir une partie de classe, struct ou méthode dans un fichier de code et une autre partie dans un fichier de code séparé.  Pour plus d'informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### Initialiseurs d'objets  
 Vous pouvez instancier et initialiser des objets de classe et de struct, ainsi que des collections d'objets, sans appeler explicitement leur constructeur.  Pour plus d'informations, consultez [Initialiseurs d'objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### Types anonymes  
 Dans les situations où ce n'est pas commode ou nécessaire de créer une classe nommée, par exemple lorsque vous remplissez une liste avec des structures de données que vous n'avez pas à rendre persistant ni à passer à une autre méthode, vous utilisez des types anonymes.  Pour plus d'informations, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### Méthodes d'extension  
 Vous pouvez étendre une classe sans créer de classe dérivée mais en créant un type séparé dont les méthodes peuvent être appelées comme si elles appartenaient au type d'origine.  Pour plus d'informations, consultez [Méthodes d'extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### Variables locales implicitement typées  
 Dans une méthode de classe ou de struct, vous pouvez utiliser le type implicite pour indiquer au compilateur de déterminer le type approprié au moment de la compilation.  Pour plus d'informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)