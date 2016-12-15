---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3000 | Microsoft Docs"
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
  - "CS3000"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3000"
ms.assetid: 37cdd3dc-8481-4e29-b78c-281baeca2d64
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3000
Les méthodes qui possèdent des arguments de variables ne sont pas conformes CLS  
  
 Les arguments utilisés dans la méthode exposent des fonctionnalités qui ne figurent pas dans les spécifications CLS \(Common Language Specifications\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
 L’exemple suivant génère l’avertissement CS3000.  
  
```  
// CS3000.cs // compile with: /target:library // CS3000 expected [assembly:System.CLSCompliant(true)] public class Test { public void AddABunchOfInts( __arglist ) {}   // CS3000 }  
```