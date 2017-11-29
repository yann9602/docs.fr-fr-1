---
title: "Comment : créer une documentation XML en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Comment : créer une documentation XML en Visual Basic
Cet exemple montre comment ajouter des commentaires de documentation XML à votre code.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Pour créer une documentation XML pour un type ou membre  
  
1.  Dans le **éditeur de Code**, placez votre curseur sur la ligne au-dessus du type ou du membre pour lequel vous souhaitez créer une documentation.  
  
2.  Type `'''` (trois guillemets simples).  
  
     Une structure XML pour le type ou le membre est ajoutée dans le **éditeur de Code**.  
  
3.  Ajouter des informations descriptives entre les balises appropriées.  
  
    > [!NOTE]
    >  Si vous ajoutez des lignes supplémentaires dans le bloc de documentation XML, chaque ligne doit commencer par `'''`.  
  
4.  Ajouter du code qui utilise le type ou le membre avec les nouveaux commentaires de documentation XML.  
  
     IntelliSense affiche le texte à partir de la \<Résumé > balise pour le type ou membre.  
  
5.  Compilez le code pour générer un fichier XML contenant les commentaires de documentation. Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation de votre code avec le langage XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
