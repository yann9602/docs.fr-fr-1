---
title: "Polymorphisme (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, polymorphisme"
  - "polymorphisme (C#)"
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# Polymorphisme (Guide de programmation C#)
Le polymorphisme est souvent considéré comme le troisième pilier d'une programmation orientée objet, après l'encapsulation et l'héritage.  Le polymorphisme est le mot grec qui signifie « plusieurs formes » et il prend deux aspects distincts :  
  
-   Au moment de l'exécution, les objets d'une classe dérivée peuvent être traités comme des objets d'une classe de base dans les paramètres de méthode et les collections ou les tableaux.  Lorsque cela se passe, le type déclaré de l'objet n'est plus identique à son type au moment de l'exécution.  
  
-   Les classes de base peuvent définir et implémenter des *méthodes* [virtuelles](../../../csharp/language-reference/keywords/virtual.md), et les classes dérivées peuvent les [substituer](../../../csharp/language-reference/keywords/override.md), ce qui signifie qu'elles fournissent leur propre définition et implémentation.  Au moment de l'exécution, quand le code client appelle la méthode, le CLR recherche le type au moment de l'exécution et appelle cette substitution de la méthode virtuelle.  C'est pourquoi, dans le code source vous pouvez appeler une méthode dans une classe de base, et provoquer l'exécution d'une version de la classe dérivée de la méthode.  
  
 Les méthodes virtuelles vous permettent d'utiliser des groupes d'objets liés de façon uniforme.  Par exemple, si vous avez une application de dessin qui permet à un utilisateur de créer différents types de formes sur une surface de dessin.  Vous ne savez pas au moment de la compilation les types de formes spécifiques que l'utilisateur va créer.  Cependant, l'application doit conserver une trace des différents types de formes créés et les mettre à jour en réponse aux actions de la souris.  Vous pouvez utiliser le polymorphisme pour résoudre ce problème en deux étapes :  
  
1.  Créer une hiérarchie de classe dans laquelle chaque classe de forme dérive d'une classe de base commune.  
  
2.  Utiliser une méthode virtuelle pour appeler la méthode appropriée dans une classe dérivée via un seul appel à la méthode de classe de base.  
  
 Tout d'abord, créez une classe de base appelée `Shape`, et des classes dérivées telles que `Rectangle`, `Circle`, et `Triangle`.  Donnez à la classe `Shape` une méthode virtuelle appelée `Draw`, et substituez\-la dans chaque classe dérivée pour dessiner une forme spécifique représentée par la classe.  Créez un objet `List<Shape>` et ajoutez\-lui un cercle, un triangle et un rectangle.  Pour mettre à jour la surface de dessin, utilisez une boucle [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pour l'itération dans la liste et appelez la méthode `Draw` dans chaque objet `Shape` de la liste.  Même si chaque objet de la liste a un type déclaré égal à `Shape`, il s'agit du type au moment de l'exécution \(la version substituée de la méthode dans chaque classe dérivée\) qui est appelé.  
  
 [!code-cs[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_1.cs)]  
  
 En C\#, chaque type est polymorphique, car tous les types, y compris les types définis par l'utilisateur, héritent de <xref:System.Object>.  
  
## Vue d'ensemble du polymorphisme  
  
### Membres virtuels  
 Quand une classe dérivée hérite d'une classe de base, elle gagne toutes les méthodes, les champs, les propriétés et les événements de la classe de base.  Le concepteur de la classe dérivée peut choisir  
  
-   de substituer les membres virtuels dans la classe de base,  
  
-   d'hériter de la méthode de classe de base la plus proche sans la substituer  
  
-   de définir une nouvelle implémentation non virtuelle de ces membres qui masque les implémentations de la classe de base  
  
 Une classe dérivée peut substituer un membre de classe de base, uniquement si le membre de classe de base est déclaré [virtuel](../../../csharp/language-reference/keywords/virtual.md) ou [abstrait](../../../csharp/language-reference/keywords/abstract.md).  Le membre dérivé doit utiliser le mot clé [override](../../../csharp/language-reference/keywords/override.md) pour indiquer explicitement que la méthode est conçue pour participer dans l'appel virtuel.  Le code suivant est fourni à titre d'exemple :  
  
 [!code-cs[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_2.cs)]  
  
 Les champs ne peuvent pas être virtuels ; seuls les méthodes, propriétés, événements et indexeurs peuvent être virtuels.  Quand une classe dérivée est substituée à un membre virtuel, ce membre est appelé lors de l'accès à une instance de cette classe en tant qu'instance de la classe de base.  Le code suivant est fourni à titre d'exemple :  
  
 [!code-cs[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_3.cs)]  
  
 Les méthodes et propriétés virtuelles permettent aux classes dérivées d'étendre une classe de base sans avoir besoin d'utiliser l'implémentation de classe de base d'une méthode.  Pour plus d'informations, consultez [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md).  Une interface fournit un autre moyen pour définir une méthode ou un ensemble de méthodes dont l'implémentation est confiée aux classes dérivées.  Pour plus d'informations, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
### Masquage des membres de classe de base par de nouveaux membres  
 Si vous voulez que votre membre dérivé ait le même nom qu'un membre dans une classe de base, mais que vous ne voulez pas qu'il participe à l'appel virtuel, vous pouvez utiliser le mot clé [new](../../../csharp/language-reference/keywords/new.md).  Le mot clé `new` est placé avec le type de retour d'un membre de classe qui est remplacé.  Le code suivant est fourni à titre d'exemple :  
  
 [!code-cs[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_4.cs)]  
  
 Les membres de classe de base masqués sont toujours accessibles à partir du code client en effectuant un cast de l'instance de la classe dérivée vers une instance de la classe de base.  Par exemple :  
  
 [!code-cs[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_5.cs)]  
  
### Empêcher les classes dérivées de remplacer les membres virtuels  
 Les membres virtuels restent virtuels indéfiniment, quel que soit le nombre de classes déclarées entre le membre virtuel et la classe qui l'a déclaré à l'origine.  Si la classe A déclare un membre virtuel, et la classe B dérive de A, et la classe C dérive de B, la classe C hérite du membre virtuel et peut le remplacer, que la classe B ait ou non déclarée une substitution pour ce membre.  Le code suivant est fourni à titre d'exemple :  
  
 [!code-cs[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_6.cs)]  
  
 Une classe dérivée peut arrêter l'héritage virtuel en déclarant une substitution [sealed](../../../csharp/language-reference/keywords/sealed.md).  Cela nécessite l'ajout du mot clé `sealed` avant le mot clé `override` dans la déclaration de membre de classe.  Le code suivant est fourni à titre d'exemple :  
  
 [!code-cs[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_7.cs)]  
  
 Dans l'exemple précédent, la méthode `DoWork` n'est plus virtuelle pour les classes dérivées de C.  Elle est toujours virtuelle pour les instances de C, même si elles sont castées en type B ou type A.  Les méthodes sealed peuvent être remplacées par des classes dérivées en utilisant le mot clé `new`, comme le montre l'exemple suivant :  
  
 [!code-cs[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_8.cs)]  
  
 Dans ce cas, si `DoWork` est appelé sur D à l'aide d'une variable de type D, le nouveau `DoWork` est appelé.  Si une variable de type C, B, ou A est utilisée pour accéder à une instance de D, un appel à `DoWork` suivra les règles de l'héritage virtuel, en routant ces appels vers l'implémentation de `DoWork` dans la classe C.  
  
### Accès aux membres virtuels de la classe de base à partir de classes dérivées  
 Une classe dérivée qui a remplacé ou substitué une méthode ou une propriété peut encore accéder à la méthode ou la propriété dans la classe de base à l'aide du mot clé base.  Le code suivant est fourni à titre d'exemple :  
  
 [!code-cs[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/polymorphism_9.cs)]  
  
 Pour plus d'informations, consultez [base](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Il est recommandé que les membres virtuels utilisent `base` pour appeler l'implémentation de classe de base de ce membre dans leur propre implémentation.  L'exécution du comportement de classe de base permet à la classe dérivée de se concentrer sur l'implémentation du comportement spécifique à la classe dérivée.  Si l'implémentation de classe de base n'est pas appelée, la classe dérivée doit rendre son comportement compatible avec le comportement de la classe de base.  
  
## Dans cette section  
  
-   [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Comment : substituer la méthode ToString](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Types](../../../csharp/programming-guide/types/index.md)