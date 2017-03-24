---
title: "/utf8output (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/utf8output"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "utf8output compiler option [C#]"
  - "/utf8output compiler option [C#]"
  - "-utf8output compiler option [C#]"
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# /utf8output (C# Compiler Options)
L'option **\/utf8output** affiche le résultat de la compilation dans le format d'encodage UTF\-8.  
  
## Syntaxe  
  
```  
/utf8output  
```  
  
## Notes  
 Avec certaines configurations internationales, la sortie du compilateur ne s'affiche pas correctement sur la console.  Le cas échéant, utilisez **\/utf8output** et redirigez la sortie du compilateur vers un fichier.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)