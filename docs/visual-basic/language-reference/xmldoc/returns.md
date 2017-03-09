---
title: "&lt;returns&gt; (Visual Basic) | Microsoft Docs"
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
  - "returns XML tag"
  - "<returns> XML tag"
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;returns&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la valeur de retour de la propriété ou de la fonction.  
  
## Syntaxe  
  
```  
<returns>description</returns>  
```  
  
#### Paramètres  
 `description`  
 Description de la valeur retournée.  
  
## Notes  
 Utilisez la balise `<returns>` dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<returns>` pour expliquer ce que la fonction `DoesRecordExist` retourne.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/returns_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)