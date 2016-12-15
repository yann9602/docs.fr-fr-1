---
title: "base (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "base"
  - "BaseClass.BaseClass"
  - "base_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "base (mot clé C#)"
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# base (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `base` sert à accéder aux membres de la classe de base à partir d'une classe dérivée :  
  
-   Appelle une méthode de la classe de base qui a été substituée par une autre méthode.  
  
-   Spécifie quel constructeur de classe de base devrait être appelé lors de la création d'instances de la classe dérivée.  
  
 L'accès à une classe de base n'est autorisé que dans un constructeur, une méthode d'instance ou un accesseur de propriété d'instance.  
  
 Le fait d'utiliser le mot clé `base` à partir d'une méthode statique constitue une erreur.  
  
 La classe de base accédée est la classe de base spécifiée dans la déclaration de classe.  Par exemple, si vous spécifiez `class ClassB : ClassA`, les membres de ClassA sont accessibles à partir de ClassB, indépendamment de la classe de base de ClassA.  
  
## Exemple  
 Dans cet exemple, la classe de base `Person` et la classe dérivée `Employee` possèdent toutes les deux une méthode nommée `Getinfo`.  En utilisant le mot clé `base`, il est possible d'appeler la méthode `Getinfo` de la classe de base à partir de la classe dérivée.  
  
 [!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]  
  
 Pour d'autres exemples, consultez [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) et [override](../../../csharp/language-reference/keywords/override.md).  
  
## Exemple  
 Cet exemple indique comment spécifier le constructeur de classe de base appelé lors de la création d'instances d'une classe dérivée.  
  
 [!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [this](../../../csharp/language-reference/keywords/this.md)