---
title: "Constructeurs d&#39;instances (Guide de programmation C#) | Microsoft Docs"
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
  - "constructeurs (C#), constructeurs d'instance"
  - "constructeurs d'instances (C#)"
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Constructeurs d&#39;instances (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les constructeurs d'instance sont utilisés pour créer et initialiser toutes les variables de membres d'instance lorsque vous utilisez l'expression [new](../../../csharp/language-reference/keywords/new.md) pour créer un objet d'une [classe](../../../csharp/language-reference/keywords/class.md).  Pour initialiser une classe [static](../../../csharp/language-reference/keywords/static.md), ou des variables static dans une classe non static, vous devez définir un constructeur static.  Pour plus d'informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 L'exemple suivant présente un constructeur d'instance pour :  
  
 [!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Dans un souci de clarté, cette classe contient des champs publics.  L'utilisation de champs publics n'est pas une pratique de programmation recommandée, car elle octroie à n'importe quelle méthode n'importe où dans un programme un accès sans restriction ni vérification aux mécanismes internes d'un objet.  Les membres Data doivent généralement être privés et doivent être accessibles uniquement par le biais de méthodes de classe et de propriétés.  
  
 Ce constructeur d'instance est appelé à chaque fois qu'un objet basé sur la classe `CoOrds` est créé.  Un constructeur comme celui\-ci, qui ne prend pas d'arguments, est appelé un *constructeur par défaut*.  Toutefois, il est souvent utile de fournir des constructeurs supplémentaires.  Par exemple, nous pouvons ajouter un constructeur à la classe `CoOrds` qui nous permet de spécifier des valeurs initiales pour les données membre :  
  
 [!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Cela autorise la création d'objets `CoOrd` avec des valeurs par défaut ou initiales spécifiques, comme suit :  
  
 [!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Si une classe n'a pas de constructeur, un constructeur par défaut est généré automatiquement et les valeurs par défaut sont utilisées pour initialiser les champs d'objet.  Par exemple, [int](../../../csharp/language-reference/keywords/int.md) est initialisé à 0.  Pour plus d'informations sur les valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  Par conséquent, parce que le constructeur par défaut de classe `CoOrds` initialise toutes les données membre à zéro, il peut être supprimé entièrement sans modification du comportement de la classe.  Un exemple complet d'utilisation de plusieurs constructeurs est fourni ultérieurement dans l'exemple 1 de cette rubrique, et un exemple d'un constructeur généré automatiquement est fourni dans l'exemple 2.  
  
 Les constructeurs d'instance peuvent servir à appeler les constructeurs d'instance des classes de base.  Le constructeur de classe peut appeler le constructeur de la classe de base par l'intermédiaire de l'initialiseur, comme suit :  
  
 [!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 Dans cet exemple, la classe `Circle` passe des valeurs représentant le rayon et la hauteur au constructeur fourni par `Shape`, duquel `Circle` est dérivé.  Un exemple complet d'utilisation de `Shape` et `Circle` apparaît dans cette rubrique en tant qu'exemple 3.  
  
## Exemple 1  
 L'exemple suivant illustre une classe possédant deux constructeurs de classe, l'un sans argument et l'autre doté de deux arguments.  
  
 [!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## Exemple 2  
 Dans cet exemple, la classe `Person` ne possède aucun constructeur, auquel cas un constructeur par défaut est fourni automatiquement, dont les champs sont initialisés sur leurs valeurs par défaut.  
  
 [!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Notez que la valeur par défaut de `age` est `0` et que celle de `name` est `null`.  Pour plus d'informations sur les valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## Exemple 3  
 L'exemple suivant illustre l'utilisation de l'initialiseur de classe de base.  La classe `Circle` est dérivée de la classe générale `Shape`, et la classe `Cylinder` est dérivée de la classe `Circle`.  Le constructeur de chaque classe dérivée utilise son initialiseur de classe de base.  
  
 [!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Pour obtenir d'autres exemples sur l'appel des constructeurs de classe de base, consultez [virtuels](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md) et [de base](../../../csharp/language-reference/keywords/base.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [statiques](../../../csharp/language-reference/keywords/static.md)