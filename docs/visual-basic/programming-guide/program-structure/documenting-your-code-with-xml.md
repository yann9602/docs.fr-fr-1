---
title: "Documenting Your Code with XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "XML, documenting code"
  - "XML comments, Visual Basic"
  - "Visual Basic code, documenting with XML"
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Documenting Your Code with XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous pouvez documenter votre code avec le langage XML.  
  
## Commentaires de documentation XML  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] offre un moyen simple pour créer automatiquement de la documentation XML pour les projets.  Vous pouvez générer automatiquement une structure XML pour vos types et vos membres, puis fournir des résumés, une documentation descriptive pour chaque paramètre, ainsi que d'autres notes.  Si la configuration est appropriée, la documentation XML est émise automatiquement dans un fichier XML portant le même nom que votre projet et une extension .xml.  Pour plus d'informations, consultez [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 Le fichier XML peut être soit consommé, soit manipulé en tant que XML.  Il se trouve dans le même répertoire que le fichier de sortie .exe ou .DLL de votre projet.  
  
 La documentation XML commence par `'''`.  Le traitement de ces commentaires s'accompagne de certaines restrictions :  
  
-   Le XML utilisé dans la documentation doit être correct.  Si le XML n'est pas correct, un avertissement est généré et le fichier de documentation contient un commentaire indiquant qu'une erreur est survenue.  
  
-   Les développeurs sont libres de créer leur propre jeu de balises.  Il existe un jeu de balises recommandé \(consultez la section « Rubriques connexes »\).  Certaines des balises recommandées ont des significations spéciales :  
  
    -   La balise \<param\> est employée pour décrire les paramètres.  Si elle est utilisée, le compilateur vérifiera que le paramètre existe et que tous les paramètres sont décrits dans la documentation.  Si la vérification échoue, il émet un avertissement.  
  
    -   L'attribut `cref` peut être rattaché à n'importe quelle balise pour fournir une référence à un élément de code.  Le compilateur vérifie l'existence de cet élément de code.  Si la vérification échoue, il émet un avertissement.  Le compilateur respecte également les instructions `Imports` lorsqu'il recherche un type décrit dans l'attribut `cref`.  
  
    -   La balise \<summary\> est employée par IntelliSense dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] pour afficher d'autres informations sur un type ou un membre.  
  
## Rubriques connexes  
 Pour plus d'informations sur la création d'un fichier XML avec des commentaires de documentation, consultez les rubriques suivantes :  
  
-   [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Processing the XML File](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Outils XML dans Visual Studio](/visual-studio/xml-tools/xml-tools-in-visual-studio)  
  
## Voir aussi  
 [Développement d’applications avec Visual Basic](../../../visual-basic/developing-apps/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)