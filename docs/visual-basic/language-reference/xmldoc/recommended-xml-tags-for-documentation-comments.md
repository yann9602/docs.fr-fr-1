---
title: "Recommended XML Tags for Documentation Comments (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlDocComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tags, XML"
  - "XML comments, recommended tags [Visual Basic]"
  - "comments, recommended XML tags"
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Recommended XML Tags for Documentation Comments (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] peut traiter les commentaires de documentation dans votre code et les place dans un fichier XML.  Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.  
  
 Les commentaires XML sont autorisés sur les constructions de code telles que les types et membres de types.  Pour les types partiels, seule une partie du type peut contenir des commentaires XML bien qu'elle ne présente aucune restriction sur le commentaire de ses membres.  
  
> [!NOTE]
>  Les commentaires de documentation ne peuvent pas être appliqués aux espaces de noms.  En effet, un seul espace de noms peut couvrir plusieurs assemblys, et il ne faut pas les charger tous en même temps.  
  
 Le compilateur traite n'importe quelle balise représentant du XML correct.  Les balises suivantes fournissent des fonctionnalités fréquemment employées dans la documentation utilisateur.  
  
||||  
|-|-|-|  
|[\<c\>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code\>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example\>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include\>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list\>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para\>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param\>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref\>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission\>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso\>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam\>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value\>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 \(<sup>1</sup> Le compilateur vérifie la syntaxe.\)  
  
> [!NOTE]
>  Si vous souhaitez que les signes "inférieur à" et "supérieur à" apparaissent dans le texte d'un commentaire de documentation, utilisez `<` et `>`.  Par exemple, la chaîne `"<text in angle brackets>"` apparaît telle que `<text in angle` `brackets>`.  
  
## Voir aussi  
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)