---
title: Exception de commentaire XML doit avoir un &#39; cref &#39; attribut
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords: BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Exception de commentaire XML doit avoir un &#39; cref &#39; attribut
Le \<exception > balise permet de documenter les exceptions qui peuvent être levées par une méthode. Requis `cref` attribut désigne le nom d’un membre qui est vérifié par le Générateur de documentation. Si le membre existe, il est converti en nom d’élément canonique dans le fichier de documentation.  
  
 **ID d’erreur :** BC42319  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter le `cref` attribut à l’exception, comme suit :  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
