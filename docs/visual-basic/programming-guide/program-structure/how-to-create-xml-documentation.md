---
title: "Comment : créer une Documentation XML en Visual Basic | Documents Microsoft"
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
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
ms.openlocfilehash: 363a20c0fce05566b61e764d05932a9dfb779f90
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Comment : créer une documentation XML en Visual Basic
Cet exemple montre comment ajouter des commentaires de documentation XML à votre code.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Pour créer une documentation XML pour un type ou membre  
  
1.  Dans le **éditeur de Code**, positionnez votre curseur sur la ligne au-dessus du type ou du membre pour lequel vous souhaitez créer la documentation.  
  
2.  Type `'''` (trois guillemets simples).  
  
     Une structure XML pour le type ou le membre est ajoutée dans le **éditeur de Code**.  
  
3.  Ajout d’informations descriptives entre les balises appropriées.  
  
    > [!NOTE]
    >  Si vous ajoutez des lignes supplémentaires dans le bloc de documentation XML, chaque ligne doit commencer par `'''`.  
  
4.  Ajouter du code qui utilise le type ou le membre avec les nouveaux commentaires de documentation XML.  
  
     IntelliSense affiche le texte de la \<résumé > balise pour le type ou membre.  
  
5.  Compilez le code pour générer un fichier XML contenant les commentaires de documentation. Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Documenter votre Code avec XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [Balises de commentaire XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
