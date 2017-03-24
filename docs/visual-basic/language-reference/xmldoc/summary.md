---
title: "&lt;Résumé&gt; (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
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
ms.openlocfilehash: ad2053e21e58c49205fe869a484cb2dffd2169ee
ms.lasthandoff: 03/13/2017

---
# <a name="ltsummarygt-visual-basic"></a>&lt;Résumé&gt; (Visual Basic)
Spécifie le résumé du membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `description`  
 Un résumé de l’objet.  
  
## <a name="remarks"></a>Remarques  
 Utilisez le `<summary>` balises pour décrire un type ou un membre de type. Utilisez [ \<notes >](../../../visual-basic/language-reference/xmldoc/remarks.md) pour ajouter des informations supplémentaires à une description de type.  
  
 Le texte de la `<summary>` balise est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans l’Explorateur d’objets. Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la Structure de Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation dans un fichier.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `<summary>` balises pour décrire la `ResetCounter` méthode et `Counter` propriété.  
  
 [!code-vb[VbVbcnXmlDocComments n °&1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
