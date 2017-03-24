---
title: "&lt;exception&gt; (Visual Basic) | Microsoft Docs"
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
  - "<exception> XML tag"
  - "exception XML tag"
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;exception&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie les exceptions qui peuvent être levées.  
  
## Syntaxe  
  
```  
<exception cref="member">description</exception>  
```  
  
#### Paramètres  
 `member`  
 Référence à une exception disponible dans l'environnement de compilation en cours.  Le compilateur vérifie que l'exception donnée existe et traduit `member` dans le nom d'élément canonique dans le code XML de sortie.  `member` doit apparaître dans des guillemets doubles \(" "\).  
  
 `description`  
 Description.  
  
## Notes  
 Utilisez les balises `<exception>` pour spécifier quelles exceptions peuvent être levées.  Cette balise est appliquée à une définition de méthode.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise les balises `<exception>` pour décrire une exception que la fonction `IntDivide` peut lever.  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)