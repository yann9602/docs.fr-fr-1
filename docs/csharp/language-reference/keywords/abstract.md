---
title: "abstract (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "abstract"
  - "abstract_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "abstract (mot clé C#)"
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# abstract (r&#233;f&#233;rence C#)
Le modificateur `abstract` indique que l'élément en cours de modification a une implémentation manquante ou incomplète.  Le modificateur abstract peut être utilisé avec des classes, des méthodes, des propriétés, des indexeurs et des événements.  Utilisez le modificateur `abstract` dans une déclaration de classe pour indiquer qu'une classe est destinée à être uniquement une classe de base d'autres classes.  Les membres marqués comme abstraits, ou inclus dans une classe abstraite, doivent être implémenté par les classes qui dérivent de la classe abstraite.  
  
## Exemple  
 Dans cet exemple, la classe `Square` doit fournir une implémentation de `Area` puisqu'elle dérive de `ShapesClass`:  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#1)]  
  
 Les classes abstraites présentent les fonctionnalités suivantes :  
  
-   Une classe abstraite ne peut pas être instanciée.  
  
-   Une classe abstraite peut contenir des méthodes abstraites et des accesseurs.  
  
-   Il est impossible de modifier une classe abstraite à l'aide du modificateur [sealed](../../../csharp/language-reference/keywords/sealed.md) car les deux modificateurs ont des significations opposées.  Le modificateur `sealed` empêche une classe d'être héritée et le modificateur `abstract` requiert qu'une classe soit héritée.  
  
-   Une classe non abstraite dérivée d'une classe abstraite doit inclure des implémentations réelles de tous les accesseurs et méthodes abstraites hérités.  
  
 Utilisez le modificateur `abstract` dans une déclaration de méthode ou de propriété pour indiquer que la méthode ou la propriété ne contient pas d'implémentation.  
  
 Les méthodes abstraites présentent les fonctionnalités suivantes :  
  
-   Une méthode abstraite est implicitement une méthode virtuelle.  
  
-   Les déclarations de méthodes abstraites sont autorisées uniquement dans les classes abstraites.  
  
-   Comme une déclaration de méthode abstraite ne fournit aucune implémentation réelle, il n'y a pas de corps de méthode ; la déclaration de méthode se termine simplement par un point\-virgule et la signature n'est pas suivie d'accolades \({ }\).  Par exemple :  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     L'implémentation est fournie par une méthode de substitution[override](../../../csharp/language-reference/keywords/override.md), qui est membre d'une classe non abstraite.  
  
-   L'utilisation des modificateurs [static](../../../csharp/language-reference/keywords/static.md) ou [virtual](../../../csharp/language-reference/keywords/virtual.md) dans une déclaration de méthode abstraite serait une erreur.  
  
 Les propriétés abstraites se comportent comme des méthodes abstraites, à l'exception des différences dans la syntaxe de déclaration et d'appel.  
  
-   L'utilisation du modificateur `abstract` sur une propriété statique est une erreur.  
  
-   Une propriété héritée abstraite peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur [override](../../../csharp/language-reference/keywords/override.md).  
  
 Pour plus d'informations sur les classes abstraites, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Une classe abstraite doit fournir une implémentation pour tous les membres d'interface.  
  
 Une classe abstraite qui implémente une interface peut mapper les méthodes d'interface sur des méthodes abstraites.  Par exemple :  
  
 [!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#2)]  
  
## Exemple  
 Dans cet exemple, la classe `DerivedClass` est dérivée d'une classe abstraite `BaseClass`.  La classe abstraite contient une méthode abstraite, `AbstractMethod`, et deux propriétés abstraites, `X` et `Y`.  
  
 [!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#3)]  
  
 Dans l'exemple précédent, si vous tentez d'instancier la classe abstraite en utilisant une instruction comme celle\-ci :  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 vous obtiendrez une erreur indiquant que le compilateur ne peut pas créer une instance de la classe abstraite 'BaseClass'.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [virtuels](../../../csharp/language-reference/keywords/virtual.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)