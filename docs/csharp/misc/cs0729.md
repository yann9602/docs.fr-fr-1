---
title: "Erreur du compilateur CS0729 | Microsoft Docs"
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
  - "CS0729"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0729"
ms.assetid: e0421d06-e818-404f-af97-d101272f4d07
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0729
Le type 'type' est défini dans cet assembly, mais un redirecteur de type est spécifié pour ce type  
  
 Vous ne pouvez pas utiliser un redirecteur de type pour un type défini dans le même assembly.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0729 :  
  
```  
// CS0729.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:TypeForwardedTo(typeof(TestClass))]   // CS0729 class TestClass {}  
```