---
title: "&lt;value&gt; (Visual Basic) | Microsoft Docs"
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
  - "<value> XML tag"
  - "value XML tag"
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;value&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la description d'une propriété.  
  
## Syntaxe  
  
```  
<value>property-description</value>  
```  
  
#### Paramètres  
 `property-description`  
 Description de la propriété.  
  
## Notes  
 Utilisez la balise `<value>` pour décrire une propriété.  Remarquez que lorsque vous ajoutez une propriété en utilisant l'Assistant Code dans l'environnement de développement Visual Studio .NET, une balise [\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md) est ajoutée pour la nouvelle propriété.  Vous devez ensuite ajouter manuellement une balise `<value>` pour décrire la valeur représentée par la propriété.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<value>` pour décrire la valeur que contient la propriété `Counter`.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)