---
title: "&lt;seealso&gt; (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cref"
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<seealso> (balise XML C#)"
  - "cref (C#)"
  - "cref (C#), voir aussi"
  - "références croisées (C#), balises"
  - "seealso (balise XML C#)"
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# &lt;seealso&gt; (Guide de programmation&#160;C#)
## Syntaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### Paramètres  
 cref \= "`member`"  
 Référence à un membre ou un champ qu'il est possible d'appeler depuis l'environnement de compilation actuel.  Le compilateur vérifie que l'élément de code donné existe et passe `member` au nom d'élément dans la sortie XML. `member` doit être placé entre guillemets doubles \(" "\).  
  
 Pour plus d'informations sur la création d'une référence cref à un type générique, consultez [\<see\>](../../../csharp/programming-guide/xmldoc/see.md).  
  
## Notes  
 La balise \<seealso\> permet de spécifier le texte que vous souhaitez voir apparaître dans une section « Voir aussi ».  Utilisez [\<see\>](../../../csharp/programming-guide/xmldoc/see.md) pour spécifier un lien à partir de l'intérieur du texte.  
  
 Compilez avec [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Pour obtenir un exemple d'utilisation de \<seealso\>, consultez [\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)