---
title: "Erreur du compilateur CS0438 | Microsoft Docs"
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
  - "CS0438"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0438"
ms.assetid: 92c91ecb-8d6a-4850-84eb-c095c3c957f1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0438
Le type 'type' dans 'module\_1' est en conflit avec l’espace de noms 'namespace' dans 'module\_2'.  
  
 Cette erreur se produit quand un type dans un fichier source est en conflit avec un espace de noms dans un autre fichier source. Cela se produit généralement quand le type et\/ou l’espace de noms proviennent d’un module ajouté. Pour résoudre cette erreur, renommez le type ou l’espace de noms à l’origine du conflit.  
  
 L’exemple suivant génère l’erreur CS0438 :  
  
 Compilez d’abord ce fichier :  
  
```  
// CS0438_1.cs // compile with: /target:module public class Util { public class A { } }  
```  
  
 Compilez ensuite ce fichier :  
  
```  
// CS0438_2.cs // compile with: /target:module namespace Util { public class A { } }  
```  
  
 Enfin, compilez ce fichier :  
  
```  
// CS0438_3.cs // compile with: /addmodule:CS0438_1.netmodule /addmodule:CS0438_2.netmodule using System; public class Test { public static void Main() { Console.WriteLine(typeof(Util.A));   // CS0438 } }  
  
```