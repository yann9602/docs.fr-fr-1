---
title: "Balises XML recommandées pour commentaires de Documentation (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6a47c12bc24864ef6ac9f80054becad98ec97f1
ms.lasthandoff: 03/13/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Étiquettes XML recommandées pour les commentaires de documentation (Visual Basic)
Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur peut traiter les commentaires de documentation dans votre code dans un fichier XML. Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.  
  
 Les commentaires XML sont autorisés sur les constructions de code telles que les types et membres de type. Pour les types partiels, qu’une partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur le commentaire de ses membres.  
  
> [!NOTE]
>  Commentaires de documentation ne peut pas être appliquées aux espaces de noms. La raison est qu’un espace de noms peut s’étendre sur plusieurs assemblys, et pas tous les assemblys doivent être chargés en même temps.  
  
 Le compilateur traite n’importe quelle balise XML valid. Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation de l’utilisateur.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<exemple >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<inclure >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<Para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<autorisation >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<Remarques >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<Retourne >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<Résumé >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<valeur >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> le compilateur vérifie la syntaxe.)  
  
> [!NOTE]
>  Si vous souhaitez des crochets pointus pour apparaître dans le texte d’un commentaire de documentation, utilisez `<` et `>`. Par exemple, la chaîne `"<text in angle brackets>"` apparaît sous la forme `<text in angle``brackets>`.  
  
## <a name="see-also"></a>Voir aussi  
 [Documenter votre Code avec XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
