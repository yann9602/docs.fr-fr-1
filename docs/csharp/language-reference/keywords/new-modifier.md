---
title: "new, modificateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "new modifier (mot clé C#)"
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# new, modificateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En cas d'utilisation comme un modificateur de déclaration, le mot clé `new` masque explicitement un membre qui est hérité d'une classe de base.  Lorsque vous masquez un membre hérité, la version dérivée du membre remplace la version de classe de base.  Bien que vous puissiez masquer des membres sans utiliser le modificateur `new`, vous obtenez un avertissement du compilateur.  Si vous utilisez `new` pour masquer explicitement un membre, il supprime cet avertissement.  
  
 Pour masquer un membre hérité, déclarez\-le dans la classe dérivée en utilisant le même nom de membre, puis modifiez\-le à l'aide du mot\-clé `new`.  Exemple :  
  
 [!code-cs[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 Dans cet exemple, `BaseC.Invoke` est masqué par `DerivedC.Invoke`.  Le champ `x` n'est pas affecté parce qu'il n'est pas masqué par un nom semblable.  
  
 Le masquage de noms par le biais de l'héritage peut prendre l'une des formes suivantes :  
  
-   En général, une constante, un champ, une propriété ou un type qui est introduit dans une classe ou une structure masque tous les membres de la classe de base qui partagent son nom.  Il existe des cas spéciaux.  Par exemple, si vous déclarez un nouveau champ avec le nom `N` pour avoir un type qui n'est pas invocable, et qu'un type de base déclare `N` en tant que méthode, le nouveau champ ne masquera pas la déclaration de base dans la syntaxe d'appel.  Pour plus d'informations, voir la [spécification du langage C\#](http://go.microsoft.com/fwlink/?LinkId=199552) \(voir la section relative à la recherche de membres dans la section « Expressions »\).  
  
-   Une méthode introduite dans une classe ou une structure masque les propriétés, les champs et les types qui partagent ce nom, dans la classe de base.  Cela masque également toutes les méthodes de la classe de base ayant la même signature.  
  
-   Un indexeur introduit dans une classe ou un struct masque tous les indexeurs de la classe de base ayant la même signature.  
  
 L'utilisation de `new` et de[override](../../../csharp/language-reference/keywords/override.md) sur le même membre est une erreur, car les deux modificateurs ont des significations mutuellement exclusives.  Le modificateur `new` crée un nouveau membre avec le même nom et entraîne le masquage du membre d'origine.  Le modificateur `override` étend l'implémentation pour un membre hérité.  
  
 L'utilisation du modificateur `new` dans une déclaration qui ne masque pas un membre hérité génère un avertissement.  
  
## Exemple  
 Dans cet exemple, une classe de base, `BaseC` et une classe dérivée, `DerivedC`, utilisent le même nom de champ `x`, masquant ainsi la valeur du champ hérité.  Cet exemple illustre l'utilisation du modificateur `new`.  Il montre aussi comment accéder aux membres masqués de la classe de base en utilisant leurs noms complets.  
  
 [!code-cs[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## Exemple  
 Dans cet exemple, une classe imbriquée masque une classe du même nom dans la classe de base.  Cet exemple illustre l'utilisation du modificateur `new` pour éliminer le message d'avertissement, ainsi que l'accès aux membres de la classe masquée à l'aide de leurs noms complets.  
  
 [!code-cs[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Si vous supprimez le modificateur `new`, le programme peut encore être compilé et exécuté, mais vous obtiendrez l'avertissement suivant :  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)