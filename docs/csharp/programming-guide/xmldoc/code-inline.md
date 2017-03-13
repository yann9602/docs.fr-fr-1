---
title: "&lt;c&gt; (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "c"
  - "<c>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<c> (balise XML C#)"
  - "c (balise XML C#)"
  - "code, marquer le texte comme (C#)"
  - "texte, marquer comme étant du code (C#)"
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# &lt;c&gt; (Guide de programmation&#160;C#)
## Syntaxe  
  
```  
<c>text</c>  
```  
  
#### Paramètres  
 `text`  
 Texte que vous souhaitez indiquer en tant que code.  
  
## Notes  
 La balise \<c\> permet d'indiquer que le texte d'une description doit être marqué comme étant du code.  Utilisez [\<code\>](../../../csharp/programming-guide/xmldoc/code.md) pour indiquer que plusieurs lignes constituent du code.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)