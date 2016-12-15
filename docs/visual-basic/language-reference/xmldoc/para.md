---
title: "&lt;para&gt; (Visual Basic) | Microsoft Docs"
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
  - "<para> XML tag"
  - "para XML tag"
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;para&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie que le contenu est mis en forme comme un paragraphe.  
  
## Syntaxe  
  
```  
<para>content</para>  
```  
  
#### Paramètres  
 `content`  
 Texte du paragraphe.  
  
## Notes  
 La balise `<para>` est à utiliser à l'intérieur d'une balise, telle que [\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md) ou [\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md) et vous permet d'ajouter une structure au texte.  
  
 Compilez avec [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation et les placer dans un fichier.  
  
## Exemple  
 Cet exemple utilise la balise `<para>` pour fractionner la section Notes de la méthode `UpdateRecord` en deux paragraphes.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## Voir aussi  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)