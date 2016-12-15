---
title: "Erreur du compilateur CS1914 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1914"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1914"
ms.assetid: e61361b6-4660-41fd-a574-cc48e1b3873c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1914
Impossible d’assigner le champ Static 'nom' dans un initialiseur d’objet  
  
 Par définition, les initialiseurs d’objets initialisent des objets, ou instances, de classes. Ils ne doivent pas être utilisés pour initialiser un champ `static` de type. Quel que soit le nombre d’instances d’une classe qui sont créés, il n’existe qu’une seule copie d’un champ `static`.  
  
### Pour corriger cette erreur  
  
1.  Remplacez le champ par un champ d’instance du type ou supprimez son initialisation de l’initialiseur d’objet.  
  
## Exemple  
 Le code suivant génère l’erreur CS1914, car l’initialiseur essaie d’initialiser le champ `TestClass.Number`, qui est de type `static` :  
  
```  
// cs1914.cs using System.Linq; public class TestClass { public string Message { get; set; } public static int Number { get; set; } } class Test { static void Main() { TestClass b = new TestClass() { Message = "Hello", Number = "555-1212" }; // CS1914 } }  
```