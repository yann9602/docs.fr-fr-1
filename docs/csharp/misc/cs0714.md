---
title: "Erreur du compilateur CS0714 | Microsoft Docs"
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
  - "CS0714"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0714"
ms.assetid: fbb5dc55-645c-4980-bf4b-3c2f84a3c6cd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0714
'static type' : les classes static ne peuvent pas implémenter d’interfaces  
  
 Les interfaces peuvent définir des méthodes non\-static sur des objets. Celles\-ci peuvent donc ne pas être implémentées par les classes static. Pour résoudre cette erreur, vérifiez que votre classe ne tente pas d’implémenter des interfaces.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0714 :  
  
```  
// CS0714.cs interface I { } public static class C : I  // CS0714 { public static void Main() { } }  
```