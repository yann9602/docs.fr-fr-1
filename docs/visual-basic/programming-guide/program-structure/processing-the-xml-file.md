---
title: Traitement du fichier XML (Visual Basic) | Documents Microsoft
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
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
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
ms.openlocfilehash: 72b2832d0131adf39a37ebd9297b43fb34ea49ba
ms.lasthandoff: 03/13/2017

---
# <a name="processing-the-xml-file-visual-basic"></a>Traitement du fichier XML (Visual Basic)
Le compilateur génère une chaîne d’identification pour chaque construction de votre code qui est marqué pour générer la documentation. (Pour plus d’informations sur la façon de balises à votre code, consultez [balises de commentaire XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) La chaîne d’ID identifie de façon unique la construction. Les programmes qui traitent le fichier XML peuvent utiliser la chaîne d’ID pour identifier le correspondant [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] élément de métadonnées/réflexion.  
  
 Le fichier XML n’est pas une représentation hiérarchique de votre code. Il est une simple liste comportant un identificateur généré pour chaque élément.  
  
 Le compilateur respecte les règles suivantes lorsqu’il génère les chaînes d’identification :  
  
-   Aucun espace blanc n’est placé dans la chaîne.  
  
-   La première partie de la chaîne d’identification identifie le type de membre identifié, avec un caractère unique suivi par un signe deux-points. Les membres suivants sont utilisés.  
  
|Caractère|Description|  
|---|---|  
|N|namespace<br /><br /> Vous ne pouvez pas ajouter des commentaires de documentation à un espace de noms, mais vous pouvez effectuer les références CREF, prise en charge.|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`|  
|F|champ :`Dim`|  
|P|propriété : `Property` (y compris les propriétés par défaut)|  
|M|method: `Sub`, `Function`, `Declare`,`Operator`|  
|E|événement :`Event`|  
|!|chaîne d’erreur<br /><br /> Le reste de la chaîne fournit des informations sur l’erreur. Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur génère des informations d’erreur pour les liens qui ne peut pas être résolus.|  
  
-   La deuxième partie de la `String` est le nom qualifié complet de l’élément, en commençant à la racine de l’espace de noms. Le nom de l’élément, ses types englobants et l’espace de noms sont séparés par des points. Si le nom de l’élément lui-même comporte des points, ils sont remplacés par le signe dièse (#). Il est supposé qu’aucun élément n’a un signe dièse directement dans son nom. Par exemple, le nom qualifié complet de le `String` constructeur serait `System.String.#ctor`.  
  
-   Pour les propriétés et méthodes, s’il existe des arguments de la méthode, la liste d’arguments entre parenthèses suit. S’il n’y a pas d’arguments, aucune parenthèse n’est présent. Les arguments sont séparés par des virgules. L’encodage de chaque argument correspond directement à son encodage dans une [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] signature.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment les chaînes d’identification pour une classe et ses membres sont générés.  
  
 [!code-vb[VbVbcnXmlDocComments&#10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
