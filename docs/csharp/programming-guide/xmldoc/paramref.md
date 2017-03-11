---
title: "&lt;paramref&gt; (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "paramref"
  - "<paramref>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<paramref> (balise XML C#)"
  - "paramref (balise XML C#)"
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# &lt;paramref&gt; (guide de programmation C#)
## Syntaxe  
  
```  
<paramref name="name"/>  
```  
  
#### Paramètres  
 `name`  
 Nom du paramètre de référence.  Mettez le nom entre guillemets doubles \(" "\).  
  
## Notes  
 La balise \<paramref\> la balise vous donne un moyen d'indiquer qu'un mot, dans les commentaires du code, par exemple dans un bloc \<summary\> ou \<remarks\>, fait référence à un paramètre.  Le fichier XML peut être traité pour mettre en forme ce mot d'une manière particulière, en gras ou en italique, par exemple.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 [!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/paramref_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)