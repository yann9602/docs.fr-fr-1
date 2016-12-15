---
title: "Erreur du compilateur CS0591 | Microsoft Docs"
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
  - "CS0591"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0591"
ms.assetid: b8acbcdb-dc66-4338-9ddd-d606e5a2c57e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0591
Valeur non valide pour l’argument de l’attribut 'attribute'  
  
 Un argument non valide ou deux arguments qui s’excluent mutuellement ont été passés à un attribut.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0591 :  
  
```  
// CS0591.cs using System; [AttributeUsage(0)]   // CS0591 class I: Attribute { } public class a { public static void Main() { } }  
```