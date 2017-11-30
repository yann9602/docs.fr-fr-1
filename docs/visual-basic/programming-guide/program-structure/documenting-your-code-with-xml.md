---
title: "Documentation de votre code avec le langage XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb1f366002c4f0c675c591d83aab1b31ef8f602
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentation de votre code avec le langage XML (Visual Basic)
Dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], vous pouvez documenter votre code à l’aide de XML  
  
## <a name="xml-documentation-comments"></a>Commentaires de documentation XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]fournit un moyen simple pour créer automatiquement de documentation XML pour les projets. Vous pouvez générer automatiquement une structure XML pour vos types et membres et puis fournissent des résumés, une documentation descriptive pour chaque paramètre et d’autres remarques. Le programme d’installation approprié, la documentation XML est émise automatiquement dans un fichier XML avec le même nom que votre projet et l’extension .xml. Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 Le fichier XML peut être consommé ou manipulé en tant que XML. Ce fichier se trouve dans le même répertoire que le fichier de sortie .exe ou .dll de votre projet.  
  
 Documentation XML commence par `'''`. Le traitement de ces commentaires présente certaines restrictions :  
  
-   La documentation doit être dans un format XML correct. Si le XML n’est pas bien formé, un avertissement est généré et le fichier de documentation contient un commentaire indiquant qu’une erreur s’est produite.  
  
-   Les développeurs sont libres de créer leur propre jeu de balises. Il existe un jeu de balises (voir « Rubriques connexes » dans cette rubrique) recommandé. Certaines des balises recommandées ont des significations spéciales :  
  
    -   La balise \<param> est utilisée pour décrire les paramètres. Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. Si la vérification échoue, le compilateur émet un avertissement.  
  
    -   L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code. Le compilateur vérifie l’existence de cet élément de code. Si la vérification échoue, le compilateur émet un avertissement. Le compilateur respecte également les `Imports` instructions lorsque vous recherchez un type décrit dans le `cref` attribut.  
  
    -   Le \<Résumé > balise est utilisée par IntelliSense dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] pour afficher des informations supplémentaires sur un type ou membre.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d’informations sur la création d’un fichier XML avec des commentaires de documentation, consultez les rubriques suivantes :  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Traitement du fichier XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Outils XML dans Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’applications avec Visual Basic](../../../visual-basic/developing-apps/index.md)  
 [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)
