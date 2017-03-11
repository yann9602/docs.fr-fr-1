---
title: "sealed (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "sealed"
  - "sealed_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sealed (mot clé C#)"
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# sealed (r&#233;f&#233;rence C#)
Lorsqu'il est appliqué à une classe, le modificateur `sealed` empêche les autres classes d'en hériter.  Dans l'exemple suivant, la classe `B` hérite de la classe `A`, mais aucune classe ne peut hériter de la classe `B`.  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 Vous pouvez également utiliser le modificateur `sealed` sur une méthode ou une propriété qui substitue une méthode ou une propriété virtuelle dans une classe de base.  Cela vous permet d'autoriser les classes à dériver de votre classe et de les empêcher de substituer des méthodes ou des propriétés virtuelles spécifiques.  
  
## Exemple  
 Dans l'exemple suivant, `Z` hérite de `Y` mais `Z` ne peut pas substituer le fonction virtuelle `F` qui est déclarée dans `X` et sealed dans `Y`.  
  
 [!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#16)]  
  
 Lorsque vous définissez de nouvelles méthodes ou propriétés dans une classe, vous pouvez empêcher les classes dérivées de les substituer en ne les déclarant pas comme [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
 L'utilisation du modificateur [abstract](../../../csharp/language-reference/keywords/abstract.md) avec une classe sealed est une erreur. En effet, une classe abstraite doit être héritée d'une classe qui fournit une implémentation des méthodes ou propriétés abstraites.  
  
 Lorsqu'il s'applique à une méthode ou une propriété, le modificateur `sealed` doit toujours être utilisé avec [override](../../../csharp/language-reference/keywords/override.md).  
  
 Comme les structs sont implicitement sealed, il est impossible d'en hériter.  
  
 Pour plus d'informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Pour plus d'exemples, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## Exemple  
 [!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#17)]  
  
 Dans l'exemple précédent, si vous tentez d'hériter de la classe sealed en utilisant une instruction telle que :  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 vous obtenez le message d'erreur :  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Notes  
 Pour déterminer s'il faut sceller une classe, méthode ou propriété, vous devez généralement considérer les deux points suivants :  
  
-   Les avantages potentiels dont les classes dérivées peuvent bénéficier en personnalisant votre classe.  
  
-   La possibilité que les classes dérivées modifient vos classes et qu'elles ne fonctionnent plus correctement ni comme prévu.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [virtuels](../../../csharp/language-reference/keywords/virtual.md)