---
title: '&lt;Param&gt; (Visual Basic) | Documents Microsoft'
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
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 41852a7fc41595050940d87f9e741df5cb23361c
ms.lasthandoff: 03/13/2017

---
# <a name="ltparamgt-visual-basic"></a>&lt;Param&gt; (Visual Basic)
Définit un nom de paramètre et une description.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 Le nom d’un paramètre de méthode. Placez le nom entre guillemets (« »).  
  
 `description`  
 Une description pour le paramètre.  
  
## <a name="remarks"></a>Remarques  
 Le `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.  
  
 Le texte de la `<param>` balise apparaît dans les emplacements suivants :  
  
-   Informations sur les paramètres d’IntelliSense. Pour plus d’informations, consultez [Utilisation d’IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).  
  
-   Explorateur d’objets. Pour plus d’informations, consultez [Affichage de la structure du code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation dans un fichier.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `<param>` balises pour décrire le `id` paramètre.  
  
 [!code-vb[VbVbcnXmlDocComments n °&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
