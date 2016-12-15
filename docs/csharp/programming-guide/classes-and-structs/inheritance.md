---
title: "H&#233;ritage (Guide de programmation C#) | Microsoft Docs"
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
  - "classes abstraites (C#)"
  - "méthodes abstraites (C#)"
  - "langage C#, héritage"
  - "classes dérivées (C#)"
  - "héritage (C#)"
  - "méthodes virtuelles (C#)"
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
caps.latest.revision: 38
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# H&#233;ritage (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'héritage, avec l'encapsulation et le polymorphisme, est l'une des trois caractéristiques principales \(ou *piliers*\) de la programmation orientée objet.  Il vous permet de créer de nouvelles classes qui réutilisent, étendent et modifient le comportement défini dans d'autres classes.  La classe dont les membres sont hérités porte le nom de *classe de base* et la classe qui hérite de ces membres porte le nom de *classe dérivée*.  Une classe dérivée ne peut avoir qu'une seule classe de base directe.  Toutefois, l'héritage est transitif.  Si ClassC est dérivé de ClassB et ClassB est dérivé de ClassA, ClassC hérite des membres déclarés dans ClassB et ClassA.  
  
> [!NOTE]
>  Les structs ne prennent pas en charge l'héritage, mais ils peuvent implémenter des interfaces.  Pour plus d'informations, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
 Conceptuellement, une classe dérivée est une spécialisation de la classe de base.  Par exemple, si vous avez une classe de base `Animal`, vous pouvez avoir une classe dérivée nommée `Mammal` et une autre classe dérivée nommée `Reptile`.  Un `Mammal` est un `Animal` et un `Reptile` est un `Animal`, mais chaque classe dérivée représente des spécialisations différentes de la classe de base.  
  
 Lorsque vous définissez une classe à dériver d'une autre classe, la classe dérivée obtient implicitement tous les membres de la classe de base, à l'exception de ses constructeurs et destructeurs.  La classe dérivée peut ainsi réutiliser le code dans la classe de base sans avoir à le réimplémenter.  Dans la classe dérivée, vous pouvez ajouter davantage de membres.  De cette manière, la classe dérivée étend la fonctionnalité de la classe de base.  
  
 L'illustration suivante montre une classe `WorkItem` qui représente un élément de travail dans un processus métier.  Comme toutes les classes, elle dérive de <xref:System.Object?displayProperty=fullName> et hérite de toutes ses méthodes.  `WorkItem` ajoute cinq de ses membres.  Cela inclut un constructeur, parce que les constructeurs ne sont pas hérités.  La classe `ChangeRequest` hérite de `WorkItem` et représente un type particulier d'élément de travail.  `ChangeRequest` ajoute deux membres supplémentaires aux membres qu'il hérite de `WorkItem` et <xref:System.Object>.  Elle doit ajouter son propre constructeur et ajoute également `originalItemID`.  La propriété `originalItemID` permet à l'instance de `ChangeRequest` d'être associée à `WorkItem` d'origine auquel la demande de modification s'applique.  
  
 ![Héritage de classe](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class\_Inheritance")  
Héritage de classe  
  
 L'exemple suivant illustre la manière dont les relations de classe démontrées dans l'illustration précédente sont exprimées en C\#.  Il indique également comment `WorkItem` substitue la méthode virtuelle <xref:System.Object.ToString%2A?displayProperty=fullName> et comment la classe `ChangeRequest` hérite de l'implémentation `WorkItem` de la méthode.  
  
 [!code-cs[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## Méthodes virtuelles et abstraites  
 Lorsqu'une classe de base déclare une méthode comme [virtuelle](../../../csharp/language-reference/keywords/virtual.md), une classe dérivée peut [substituer](../../../csharp/language-reference/keywords/override.md) la méthode avec sa propre implémentation.  Si une classe de base déclare un membre comme [abstrait](../../../csharp/language-reference/keywords/abstract.md), cette méthode doit être substituée dans toute classe non abstraite qui hérite directement de cette classe.  Si une classe dérivée est elle\-même abstraite, elle hérite des membres abstraits sans les implémenter.  Les membres virtuels et abstraits sont la base du polymorphisme, qui est la deuxième caractéristique principale de la programmation orientée objet.  Pour plus d'informations, consultez [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## Classes de base abstraites  
 Vous pouvez déclarer une classe comme [abstraite](../../../csharp/language-reference/keywords/abstract.md) si vous souhaitez empêcher l'instanciation directe au moyen du mot clé [new](../../../csharp/language-reference/keywords/new.md) .  Dans ce cas, la classe peut être utilisée uniquement si une classe nouvelle est dérivée d'elle.  Une classe abstraite peut contenir une ou plusieurs signatures de méthode qui elles\-mêmes sont déclarées comme abstraites.  Ces signatures spécifient les paramètres et valeurs de retour, mais n'ont aucune implémentation \(corps de méthode\).  Il n'est pas obligatoire qu'une classe abstraite contienne des membres abstraits ; toutefois, si une classe contient un membre abstrait, la classe elle\-même doit être déclarée comme abstraite.  Les classes dérivées qui ne sont pas elles\-mêmes abstraites doivent fournir l'implémentation pour toute méthode abstraite à partir d'une classe de base abstraite.  Pour plus d'informations, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## Interfaces  
 Une *interface* est un type référence quelque peu semblable à une classe de base abstraite qui se compose uniquement de membres abstraits.  Lorsqu'une classe implémente une interface, elle doit fournir une implémentation pour tous les membres de l'interface.  Une classe peut implémenter plusieurs interfaces, bien qu'elle puisse dériver d'une classe de base directe unique.  
  
 Les interfaces sont utilisées pour définir des fonctions spécifiques pour les classes qui n'ont pas nécessairement de relation « est un ».  Par exemple, l'interface <xref:System.IEquatable%601?displayProperty=fullName> peut être implémentée par toute classe ou tout struct qui doit permettre au code client de déterminer si deux objets du type sont équivalents \(quelle que soit la façon dont le type définit l'équivalence\).  <xref:System.IEquatable%601> n'implique pas le même type de relation « est un » que celle qui existe entre une classe de base et une classe dérivée \(par exemple, un `Mammal` est un `Animal`\).  Pour plus d'informations, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
## Accès de classe dérivée aux membres de la classe de base  
 Une classe dérivée a accès aux membres publics, protégés, internes et internes protégés d'une classe de base.  Bien qu'une classe dérivée hérite des membres privés d'une classe de base, elle ne peut pas accéder à ces membres.  Toutefois, tous ces membres privés sont quand même présents dans la classe dérivée et peuvent effectuer le même travail que dans la classe de base elle\-même.  Par exemple, supposez qu'une méthode de classe de base protégée accède à un champ privé.  Ce champ doit être présent dans la classe dérivée pour que la méthode de classe de base héritée fonctionne correctement.  
  
## Empêcher la dérivation supplémentaire  
 Une classe peut empêcher d'autres classes d'hériter d'elle, ou de l'un de ses membres, en se déclarant elle\-même ou le membre comme [sealed](../../../csharp/language-reference/keywords/sealed.md).  Pour plus d'informations, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## Masquage des membres de la classe de base par la classe héritée  
 Une classe dérivée peut masquer des membres de la classe de base en déclarant ces membres avec les mêmes nom et signature.  Le modificateur [new](../../../csharp/language-reference/keywords/new.md) peut être utilisé pour indiquer explicitement que le membre n'est pas censé être une substitution du membre de base.  L'utilisation de [new](../../../csharp/language-reference/keywords/new.md) n'est pas obligatoire, mais un avertissement du compilateur est généré si [new](../../../csharp/language-reference/keywords/new.md) n'est pas utilisé.  Pour plus d'informations, consultez [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)