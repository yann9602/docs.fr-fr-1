---
title: "&lt;seealso&gt; (Visual Basic) | Microsoft Docs"
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
  - "<seealso> XML tag"
  - "seealso XML tag"
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;seealso&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie un lien qui apparaît à la section Voir aussi.  
  
## Syntaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### Paramètres  
 `member`  
 Référence à un membre ou un champ qu'il est possible d'appeler depuis l'environnement de compilation actuel.  Le compilateur vérifie que l'élément de code donné existe et passe `member` au nom d'élément dans le XML de sortie.  `member` doit apparaître dans des guillemets doubles \(" "\).  
  
## Notes  
 Utilisez les balises `<seealso>` pour spécifier le texte que vous souhaitez voir apparaître à la section Voir aussi.  Utilisez [\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) pour spécifier un lien à partir de l'intérieur du texte.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise les balises `<seealso>` dans la section Notes `DoesRecordExist` pour faire référence à la méthode `UpdateRecord`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/seealso_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)