---
title: "/preferreduilang (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/preferreduilang"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "preferreduilang compiler option [C#]"
  - "/preferreduilang compiler option [C#]"
  - "-preferreduilang compiler option [C#]"
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /preferreduilang (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En utilisant l'option du compilateur `/preferreduilang`, vous pouvez spécifier la langue dans laquelle le compilateur c affiche la sortie, tels que les messages d'erreur.  
  
## Syntaxe  
  
```  
/preferreduilang: language  
```  
  
## Arguments  
 `language`  
 Le [nom de la langue](http://go.microsoft.com/fwlink/p/?LinkId=236992) du langage à utiliser pour la sortie du compilateur.  
  
## Notes  
 Vous pouvez utiliser l'option du compilateur `/preferreduilang` pour spécifier la langue que vous souhaitez le compilateur c à utiliser pour les messages d'erreur et une autre sortie de ligne de commande.  Si le module linguistique pour la langue n'est pas installé, le paramètre de langue du système d'exploitation est utilisé à la place, et aucune erreur n'est stockée.  
  
```c#  
csc.exe /preferreduilang:ja-JP  
```  
  
## Configuration requise  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)