---
title: "Avertissement du compilateur (niveau&#160;1) CS1682 | Microsoft Docs"
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
  - "CS1682"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1682"
ms.assetid: 6f3b19ba-29f3-4472-941d-57f6fda6dc3a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1682
La référence au type 'type' déclare être imbriquée dans 'type imbriqué', mais elle est introuvable  
  
 Cette erreur se produit quand vous importez des références qui ne s’accordent pas avec d’autres références ou avec le code que vous avez écrit. Cette erreur est souvent obtenue quand vous écrivez du code qui fait référence à une classe dans des métadonnées et que vous supprimez cette classe ou modifiez sa définition par la suite.  
  
## Exemple  
  
```  
// CS1682.cs // compile with: /target:library /keyfile:mykey.snk public class A { public class N1 {} }  
```  
  
## Exemple  
  
```  
// CS1682_b.cs // compile with: /target:library /reference:CS1682.dll using System; public class Ref { public static A A1() { return new A(); } public static A.N1 N1() { return new A.N1(); } }  
```  
  
## Exemple  
  
```  
// CS1682_c.cs // compile with: /target:library /keyfile:mykey.snk /out:CS1682.dll public class A { public void M1() {} }  
```  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1682 :  
  
```  
// CS1682_d.cs // compile with: /reference:CS1682.dll /reference:CS1682_b.dll /W:1 // CS1682 expected class Tester { static void Main() { Ref.A1().M1(); } }  
```