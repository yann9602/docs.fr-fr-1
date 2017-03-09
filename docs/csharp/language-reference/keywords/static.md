---
title: "static (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "static"
  - "static_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "static (mot clé C#)"
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# static (r&#233;f&#233;rence C#)
Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui\-même plutôt qu'à un objet spécifique.  Le modificateur `static` peut être utilisé avec des classes, champs, méthodes, propriétés, opérateurs, événements et constructeurs, mais il ne peut pas être utilisé avec des indexeurs, des destructeurs ou des types autres que des classes.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## Exemple  
 La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :  
  
 [!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#18)]  
  
 Une déclaration de constante ou de type est de manière implicite un membre statique.  
  
 Un membre statique ne peut pas être référencé par le biais d'une instance.  À la place, il est référencé à l'aide du nom de type.  Par exemple, considérons la classe suivante :  
  
 [!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#19)]  
  
 Pour faire référence au membre statique `x`, utilisez le nom complet `MyBaseC.MyStruct.x` \(à moins qu'il soit accessible à partir de la même portée\) :  
  
```c#  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Alors qu'une instance de classe contient une copie distincte de tous les champs d'instances de la classe, il existe une seule copie de chaque champ statique.  
  
 Il est impossible d'utiliser [this](../../../csharp/language-reference/keywords/this.md) pour référencer des méthodes statiques ou des accesseurs de propriétés.  
  
 Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être statiques.  
  
 Les classes et les classes statiques peuvent avoir des constructeurs statiques.  Les constructeurs statiques sont appelés à un moment donné situé entre le début du programme et l'instanciation de la classe.  
  
> [!NOTE]
>  L'utilisation du mot clé `static` est plus limitée qu'en C\+\+.  Pour comparer avec le mot clé en C\+\+, consultez [Statique](/visual-cpp/misc/static-cpp).  
  
 Pour illustrer les membres statiques, considérez une classe qui représente un employé d'une entreprise.  Partez de l'hypothèse que la classe contient une méthode permettant de compter les employés et un champ pour stocker le nombre d'employés.  La méthode et le champ n'appartiennent à aucun employé d'instance.  À la place, ils appartiennent à la classe de l'entreprise.  En conséquence, ils doivent être déclarés comme membres statiques de la classe.  
  
## Exemple  
 Dans cet exemple, le code lit le nom et l'identificateur d'un nouvel employé, incrémente d'une unité le compteur d'employés et affiche les informations concernant le nouvel employé et le nouveau nombre d'employés.  Par souci de simplicité, ce programme lit le nombre actuel d'employés à partir du clavier.  Dans une application réelle, cette information doit être lue à partir d'un fichier.  
  
 [!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#20)]  
  
## Exemple  
 Cet exemple montre que, bien qu'il soit possible d'initialiser un champ statique à l'aide d'un autre champ statique non encore déclaré, les résultats seront indéfinis jusqu'à vous affectiez explicitement une valeur au champ statique.  
  
 [!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#21)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)