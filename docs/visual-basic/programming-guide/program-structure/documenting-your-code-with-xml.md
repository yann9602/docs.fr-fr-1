---
title: Documenter votre Code avec XML (Visual Basic) | Documents Microsoft
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
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
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
ms.openlocfilehash: 2ec4907ff96a0861f97de21bdf45662c558d0a95
ms.lasthandoff: 03/13/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentation de votre code avec le langage XML (Visual Basic)
Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous pouvez documenter votre code à l’aide de XML  
  
## <a name="xml-documentation-comments"></a>Commentaires de documentation XML  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit un moyen simple de créer automatiquement de documentation XML pour les projets. Vous pouvez générer automatiquement une structure XML pour vos types et membres et puis fournir des résumés, une documentation descriptive pour chaque paramètre et d’autres notes. La configuration est appropriée, la documentation XML est émise automatiquement dans un fichier XML portant le même nom que votre projet et l’extension .xml. Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 Le fichier XML peut être consommé ou manipulé en tant que XML. Ce fichier se trouve dans le même répertoire que le fichier de sortie .exe ou .dll de votre projet.  
  
 Documentation XML commence par `'''`. Le traitement de ces commentaires présente certaines restrictions :  
  
-   La documentation doit être correcte XML. Si le XML n’est pas correct, un avertissement est généré et le fichier de documentation contient un commentaire indiquant qu’une erreur est survenue.  
  
-   Les développeurs sont libres de créer leur propre jeu de balises. Il existe un jeu de balises (voir « Rubriques connexes » dans cette rubrique) recommandé. Certaines des balises recommandées ont des significations spéciales :  
  
    -   Le \<param > balise est utilisée pour décrire les paramètres. Si utilisé, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation. Si la vérification échoue, le compilateur émet un avertissement.  
  
    -   Le `cref` attribut pouvant être joints à n’importe quelle balise pour fournir une référence à un élément de code. Le compilateur vérifie l’existence de cet élément de code. Si la vérification échoue, le compilateur émet un avertissement. Le compilateur respecte également les `Imports` instructions lorsqu’il recherche un type décrit dans le `cref` attribut.  
  
    -   Le \<résumé > balise est employée par IntelliSense dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] pour afficher des informations supplémentaires sur un type ou membre.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d’informations sur la création d’un fichier XML avec des commentaires de documentation, consultez les rubriques suivantes :  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Traitement du fichier XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Outils XML dans Visual Studio](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’Applications avec Visual Basic](../../../visual-basic/developing-apps/index.md)   
 [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)
