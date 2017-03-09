---
title: "Classes (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "classes [C#]"
  - "Langage C#, classes"
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 40
---
# Classes (guide de programmation C#)
Une *classe* est une construction qui vous permet de créer vos propres types personnalisés en regroupant des variables d'autres types, méthodes et événements.  Une classe s'apparente à un plan.  Elle définit les données et le comportement d'un type.  Si la classe n'est pas déclarée comme statique, le code client peut l'utiliser en créant des *objets* ou des *instances* assignés à une variable.  La variable reste en mémoire jusqu'à toutes les références à elle soient hors de portée.  À ce stade, le CLR la marque comme admissible pour le garbage collection.  Si la classe est déclarée comme [statique](../../../csharp/language-reference/keywords/static.md), il existe une seule copie en mémoire et le code client peut y accéder uniquement par le biais de la classe elle\-même, et non par une *variable d'instance*.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 À la différence des structs, les classes prennent en charge l'*héritage*, caractéristique fondamentale de la programmation orientée objet.  Pour plus d'informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## Déclaration de classes  
 Les classes sont déclarées à l'aide du mot clé [class](../../../csharp/language-reference/keywords/class.md), comme illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/classes_1.cs)]  
  
 Le mot clé `class` est précédé par le niveau d'accès.  [public](../../../csharp/language-reference/keywords/public.md) étant utilisé dans ce cas, n'importe qui peut créer des objets à partir de cette classe.  Le nom de la classe suit le mot clé `class`.  Le reste de la définition est le corps de la classe, où le comportement et les données sont définis.  Les champs, propriétés, méthodes et événements d'une classe sont désignés collectivement par le terme *membres de classe*.  
  
## Création d'objets  
 Bien qu'ils soient quelquefois utilisés l'un à la place de l'autre, une classe et un objet sont des choses différentes.  Une classe définit un type d'objet, mais il ne s'agit pas d'un objet en soi.  Un objet est une entité concrète basée sur une classe ; quelquefois appelé une instance d'une classe.  
  
 Les objets peuvent être créés à l'aide du mot clé [new](../../../csharp/language-reference/keywords/new.md) suivi du nom de la classe sur lequel l'objet sera basé, comme suit :  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/classes_2.cs)]  
  
 Lorsqu'une instance d'une classe est créée, une référence à l'objet est renvoyée au programmeur.  Dans l'exemple précédent, `object1` est une référence à un objet qui est basé sur `Customer`.  Cette référence fait référence au nouvel objet, mais ne contient pas les données d'objet elles\-mêmes.  En fait, vous pouvez créer une référence d'objet sans créer d'objet du tout :  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/classes_3.cs)]  
  
 Nous ne recommandons pas de créer des références d'objet comme celle\-ci, qui ne fait pas référence à un objet, car la tentative d'accès à un objet par le biais d'une telle référence échouera au moment de l'exécution.  Toutefois, une telle référence peut être faite pour faire référence à un objet, soit en créant un objet, soit en l'assignant à un objet existant, tel que le suivant :  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/classes_4.cs)]  
  
 Ce code crée deux références d'objet qui font toutes deux référence au même objet.  Par conséquent, toute modification apportée à l'objet via `object3` sera reflétée dans les utilisations suivantes de `object4`.  Les objets qui sont basés sur des classes étant désignés par référence, les classes sont connues comme des types référence.  
  
## Héritage de classe  
 L'héritage se fait par le biais d'une *dérivation*, ce qui signifie qu'une classe est déclarée à l'aide d'une *classe de base* à partir de laquelle elle hérite des données et comportement.  Une classe de base est spécifiée en ajoutant deux\-points et le nom de la classe de base après le nom de la classe dérivée, comme suit :  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/classes_5.cs)]  
  
 Lorsqu'une classe déclare une classe de base, elle hérite de tous les membres de la classe de base à l'exception des constructeurs.  
  
 Contrairement à C\+\+, une classe en C\# peut hériter directement uniquement d'une classe de base.  Toutefois, une classe de base pouvant elle\-même hériter d'une autre classe, une classe peut hériter indirectement de plusieurs classes de base.  En outre, une classe peut implémenter directement plusieurs interfaces.  Pour plus d'informations, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
 Une classe peu être déclarée comme [abstraite](../../../csharp/language-reference/keywords/abstract.md).  Une classe abstraite contient des méthodes abstraites qui ont une définition de signature mais aucune implémentation.  Les classes abstraites ne peuvent pas être instanciées.  Elles peuvent être utilisées uniquement à travers des classes dérivées qui implémentent les méthodes abstraites.  En revanche, une classe [sealed](../../../csharp/language-reference/keywords/sealed.md) ne permet pas à d'autres classes de dériver d'elle.  Pour plus d'informations, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Les définitions de classe peuvent être fractionnées entre différents fichiers sources.  Pour plus d'informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## Description  
 Dans l'exemple suivant, une classe publique qui contient un seul champ, une méthode et une méthode spéciale appelée un constructeur est définie.  Pour plus d'informations, consultez [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md).  La classe est ensuite instanciée avec le mot clé `new`.  
  
## Exemple  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/classes_6.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Programmation orientée objet dans Visual Basic](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [Membres](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [Objets](../../../csharp/programming-guide/classes-and-structs/objects.md)