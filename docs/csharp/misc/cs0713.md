---
title: "Erreur du compilateur CS0713 | Microsoft Docs"
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
  - "CS0713"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0713"
ms.assetid: 27a46765-d982-43ba-909f-9278e26b80d2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0713
La classe statique 'static type' ne peut pas dériver du type 'type'. Les classes statiques doivent dériver d’objets.  
  
 Si cela était permis, la classe ne serait pas statique, car elle hériterait de méthodes et de membres non statiques de la classe de base. Par conséquent, cela n’est pas autorisé.  
  
 L’exemple suivant génère l’erreur CS0713 :  
  
```  
// CS0713.cs public class Base { } public static class Derived : Base  // CS0713 { } public class CMain { public static void Main() { } }  
```