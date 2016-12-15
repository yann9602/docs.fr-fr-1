---
title: "virtual (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "virtual_CSharpKeyword"
  - "virtual"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "virtual (mot clé C#)"
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# virtual (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `virtual` sert à modifier une méthode, une propriété, un indexeur ou une déclaration de l'événement et leur permet d'être substitués dans une classe dérivée.  Par exemple, cette méthode peut être substituée par toute classe qui en hérite :  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 L'implémentation d'un membre virtual peut être modifiée par un [membre de substitution](../../../csharp/language-reference/keywords/override.md) dans une classe dérivée.  Pour plus d'informations sur l'utilisation du mot clé `virtual`, consultez [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Notes  
 Lorsqu'une méthode virtuelle est appelée, un membre de substitution est recherché dans le type d'objet au moment de l'exécution.  Le membre de substitution de la classe la plus dérivée est appelé \(cela peut être le membre d'origine\), si aucune classe dérivée n'a substitué le membre.  
  
 Par défaut, les méthodes ne sont pas virtual.  Vous ne pouvez pas substituer une méthode non virtuelle.  
  
 Vous ne pouvez pas utiliser le modificateur `virtual` avec les modificateurs `static`, `abstract, private` ou `override`.  L'exemple suivant affiche une propriété virtuelle :  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Les propriétés virtual se comportent comme les méthodes abstraites, à l'exception des différences dans la syntaxe de déclaration et d'appel.  
  
-   L'utilisation du modificateur `virtual` sur une propriété statique est une erreur.  
  
-   Une propriété virtual héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur `override`.  
  
## Exemple  
 Dans cet exemple, la classe `Shape` contient les deux coordonnées `x` et `y`, ainsi que la méthode virtuelle `Area()`.  Différentes classes de formes, telles que `Circle`, `Cylinder` et `Sphere`, héritent de la classe `Shape`, et la surface est calculée pour chaque figure.  Chaque classe dérivée possède sa propre implémentation de substitution de `Area()`.  
  
 Notez que les classes héritées `Circle`, `Sphere`, et `Cylinder` tous les constructeurs d'utilisation qui initialisent la classe de base, comme indiqué dans la déclaration suivante.  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Le programme suivant calcule et affiche la zone appropriée pour chaque illustration en appelant l'implémentation appropriée de la méthode d' `Area()` , selon l'objet associé à la méthode.  
  
 [!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [new](../../../csharp/language-reference/keywords/new.md)