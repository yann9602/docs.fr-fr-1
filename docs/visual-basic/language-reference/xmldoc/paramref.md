---
title: "&lt;paramref&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
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
  - "paramref XML tag"
  - "<paramref> XML tag"
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;paramref&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Met en forme un mot comme un paramètre.  
  
## Syntaxe  
  
```  
<paramref name="name"/>  
```  
  
#### Paramètres  
 `name`  
 Nom du paramètre de référence.  Mettez le nom entre guillemets doubles \(" "\).  
  
## Notes  
 La balise `<paramref>` vous permet d'indiquer qu'un mot est un paramètre.  Le fichier XML peut être traité de manière à ce que ce paramètre ait un format bien distinct.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<paramref>` pour faire référence au paramètre `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/paramref_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)