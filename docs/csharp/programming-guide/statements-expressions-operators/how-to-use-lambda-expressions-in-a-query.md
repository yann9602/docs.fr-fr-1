---
title: "Comment&#160;: utiliser des expressions lambda dans une requ&#234;te (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressions lambda (C#), dans LINQ"
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# Comment&#160;: utiliser des expressions lambda dans une requ&#234;te (Guide de programmation&#160;C#)
Vous n'utilisez pas d'expressions lambda directement dans la syntaxe de requête, mais vous les utilisez dans les appels de méthode et les expressions de requête peuvent contenir des appels de méthode.  En fait, certaines opérations de requête peuvent être exprimées uniquement dans la syntaxe de méthode.  Pour plus d'informations sur la différence entre la syntaxe de requête et la syntaxe de méthode, consultez [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## Exemple  
 L'exemple suivant montre comment utiliser une expression lambda dans une requête fondée sur une méthode à l'aide de l'opérateur de requête standard <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName>.  Notez que la méthode <xref:System.Linq.Enumerable.Where%2A> dans cet exemple a un paramètre d'entrée du type délégué <xref:System.Func%601> et que ce délégué accepte un entier comme entrée et retourne un booléen.  L'expression lambda peut être convertie en ce délégué.  Si c'était une requête [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] qui avait utilisé la méthode <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>, le type de paramètre serait un `Expression<Func\<int,bool>>`, mais l'expression lambda se présenterait exactement sous la même forme.  Pour plus d'informations sur le type Expression, consultez <xref:System.Linq.Expressions.Expression?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#1)]  
  
## Exemple  
 L'exemple suivant montre comment utiliser une expression lambda dans un appel de méthode d'une expression de requête.  Le lambda est nécessaire, car l'opérateur de requête standard <xref:System.Linq.Enumerable.Sum%2A> ne peut pas être appelé à l'aide de la syntaxe de requête.  
  
 La requête regroupe d'abord les étudiants d'après leur niveau de notes, comme défini dans l'enum `GradeLevel`.  Puis, pour chaque, il ajoute les notes totales de chaque étudiant.  Cela requiert deux opérations `Sum`.  La `Sum` interne calcule la note totale pour chaque étudiant, et le `Sum` calcule un total combiné cumulé pour tous les étudiants du groupe.  
  
 [!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#2)]  
  
## Compilation du code  
 Pour exécuter ce code, copiez et collez la méthode dans le `StudentClass` qui est fourni dans [Comment : interroger une collection d'objets](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md), et appelez\-la à partir de la méthode `Main`.  
  
## Voir aussi  
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)