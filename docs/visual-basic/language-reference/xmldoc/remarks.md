---
title: "&lt;remarks&gt; (Visual Basic) | Microsoft Docs"
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
  - "<remarks> XML tag"
  - "remarks XML tag"
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;remarks&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie une section Notes pour le membre.  
  
## Syntaxe  
  
```  
<remarks>description</remarks>  
```  
  
#### Paramètres  
 `description`  
 Description du membre.  
  
## Notes  
 La balise `<remarks>` permet d'ajouter des informations sur un type et de compléter les informations spécifiées par [\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md).  
  
 Ces informations s'affichent dans l'Explorateur d'objets.  Pour plus d'informations sur l'Explorateur d'objets, consultez [Affichage de la structure du code](/visual-studio/ide/viewing-the-structure-of-code).  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<remarks>` pour expliquer le rôle de la méthode `UpdateRecord` retourne.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)