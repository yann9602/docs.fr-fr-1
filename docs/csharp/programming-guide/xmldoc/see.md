---
title: "&lt;see&gt; (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<see>"
  - "see"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<see> (balise XML C#)"
  - "cref (C#), <see> (balise)"
  - "références croisées (C#)"
  - "see (balise XML C#)"
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &lt;see&gt; (Guide de programmation&#160;C#)
## Syntaxe  
  
```  
<see cref="member"/>  
```  
  
#### Paramètres  
 cref \= " `member`"  
 Référence à un membre ou un champ qu'il est possible d'appeler depuis l'environnement de compilation actuel.  Le compilateur vérifie que l'élément de code donné existe et passe `member` au nom d'élément dans le XML de sortie.Placez le *membre* entre guillemets doubles \(""\).  
  
## Notes  
 La balise \<see\> permet de spécifier un lien à partir de l'intérieur du texte.  Utilisez [\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md) pour indiquer que le texte doit être placé dans une section « Voir aussi ».  Utilisez [attribut cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) pour créer des liens hypertexte internes aux pages de documentation pour les éléments de code.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
 L'exemple suivant affiche une balise \<voir\> dans une section Résumé.  
  
 [!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)