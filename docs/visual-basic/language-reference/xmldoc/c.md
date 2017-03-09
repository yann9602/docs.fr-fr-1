---
title: "&lt;c&gt; (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "c XML tag"
  - "<c> XML tag"
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;c&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Indique que le texte d'une description constitue du code.  
  
## Syntaxe  
  
```  
<c>text</c>  
```  
  
#### Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`text`|Texte que vous souhaitez indiquer en tant que code.|  
  
## Notes  
 La balise `<c>` permet d'indiquer que le texte d'une description doit être marqué comme étant du code.  Utilisez [\<code\>](../../../visual-basic/language-reference/xmldoc/code.md) pour indiquer que plusieurs lignes constituent du code.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<c>` dans la section sommaire pour indiquer que `Counter` constitue du code.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/c_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)