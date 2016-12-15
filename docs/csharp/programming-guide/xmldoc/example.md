---
title: "&lt;example&gt; (guide de programmation C#) | Microsoft Docs"
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
  - "<example>"
  - "example"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<example> (balise XML C#)"
  - "example (balise XML C#)"
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;example&gt; (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Syntaxe  
  
```  
<example>description</example>  
```  
  
#### Paramètres  
 `description`  
 Description de l'exemple de code.  
  
## Notes  
 La balise \<example\> vous permet de spécifier un exemple d'utilisation d'une méthode ou de tout autre membre de bibliothèque.  Cela implique généralement l'utilisation de la balise [\<code\>](../../../csharp/programming-guide/xmldoc/code.md).  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/example_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)