---
title: "How to: Create XML Documentation in Visual Basic | Microsoft Docs"
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
  - "XML comments"
  - "XML documentation, creating"
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Create XML Documentation in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Cet exemple explique comment ajouter à votre code des commentaires de documentation XML.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour créer la documentation XML pour un type ou un membre  
  
1.  Dans l'**éditeur de code**, positionnez votre curseur sur la ligne au\-dessus du type ou du membre pour lequel vous souhaitez créer la documentation.  
  
2.  Tapez `'''` \(trois guillemets simples\).  
  
     Une structure XML pour le type ou le membre est ajoutée dans l'**éditeur de code**.  
  
3.  Ajoutez des informations descriptives entre les balises appropriées.  
  
    > [!NOTE]
    >  Si vous ajoutez des lignes supplémentaires dans le bloc de documentation XML, chaque ligne doit commencer par `'''`.  
  
4.  Ajoutez du code supplémentaire qui utilise le type ou le membre avec les nouveaux commentaires de documentation XML.  
  
     IntelliSense affiche le texte de la balise \<summary\> pour le type ou le membre.  
  
5.  Compilez le code pour générer un fichier XML qui contient les commentaires de documentation.  Pour plus d'informations, consultez [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## Voir aussi  
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)