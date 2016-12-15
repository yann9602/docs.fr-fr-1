---
title: "Erreur du compilateur CS0633 | Microsoft Docs"
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
  - "CS0633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0633"
ms.assetid: a24d310b-151a-45eb-b150-3407940ec24c
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0633
L’argument de l’attribut 'attribut' doit être un identificateur valide  
  
 Les arguments que vous passez aux attributs <xref:System.Diagnostics.ConditionalAttribute> ou <xref:System.Runtime.CompilerServices.IndexerNameAttribute> doivent être des identificateurs valides. Cela signifie qu’ils ne peuvent pas contenir de caractères, tels que le signe « \+ », qui ne sont pas autorisés dans les identificateurs.  
  
## Exemple  
 Cet exemple montre l’erreur CS0633 avec l’utilisation de <xref:System.Diagnostics.ConditionalAttribute>. L’exemple suivant génère l’erreur CS0633 :  
  
```  
// CS0633a.cs #define DEBUG using System.Diagnostics; public class Test { [Conditional("DEB+UG")]   // CS0633 // try the following line instead // [Conditional("DEBUG")] public static void Main() { } }  
```  
  
## Exemple  
 Cet exemple montre l’erreur CS0633 avec l’utilisation de <xref:System.Runtime.CompilerServices.IndexerNameAttribute>.  
  
```  
// CS0633b.cs // compile with: /target:module #define DEBUG using System.Runtime.CompilerServices; public class Test { [IndexerName("Invalid+Identifier")]   // CS0633 // try the following line instead // [IndexerName("DEBUG")] public int this[int i] { get { return i; } } }  
  
```