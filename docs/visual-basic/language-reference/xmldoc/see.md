---
title: "&lt;see&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "see XML tag"
  - "<see> XML tag"
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;see&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie un lien vers un autre membre.  
  
## Syntaxe  
  
```  
<see cref="member"/>  
```  
  
#### Paramètres  
 `member`  
 Référence à un membre ou un champ qu'il est possible d'appeler depuis l'environnement de compilation actuel.  Le compilateur vérifie que l'élément de code donné existe et passe `member` au nom d'élément dans le XML de sortie.  `member` doit apparaître dans des guillemets doubles \(" "\).  
  
## Notes  
 Utilisez la balise `<see>` pour spécifier un lien à partir de l'intérieur du texte.  Utilisez [\<seealso\>](../../../visual-basic/language-reference/xmldoc/seealso.md) pour indiquer du texte que vous souhaitez voir apparaître dans une section « Voir aussi ».  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise les balises `<see>` dans la section Notes `UpdateRecord` pour faire référence à la méthode `DoesRecordExist`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)