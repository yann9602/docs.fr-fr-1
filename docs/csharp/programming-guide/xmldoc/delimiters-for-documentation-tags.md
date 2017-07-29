---
title: "Délimiteurs pour les balises de documentation (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3e31f0c3d815c0454a9be6813ff9a04e5fa4c7de
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Délimiteurs pour les balises de documentation (Guide de programmation C#)
L’utilisation de commentaires de documentation XML exige des délimiteurs, qui indiquent au compilateur où un commentaire de documentation commence et se termine. Vous pouvez utiliser les genres de délimiteurs ci-dessous avec les balises de documentation XML :  
  
 `///`  
 Délimiteur à une ligne. Il s’agit de la forme illustrée dans les exemples de documentation et utilisée par les modèles de projet Visual C#. Si un caractère espace blanc suit le délimiteur, ce caractère n’est pas inclus dans la sortie XML.  
  
> [!NOTE]
>  L’IDE Visual Studio offre une fonctionnalité d’édition de commentaire intelligente, qui insère automatiquement les balises \<summary> et \</summary>, et place le curseur dans ces balises quand vous tapez le délimiteur `///` dans l’Éditeur de code. Vous pouvez accéder à cette fonctionnalité à partir d’[Options, Éditeur de texte, C#, Mise en forme](/visualstudio/ide/reference/options-text-editor-csharp-formatting) dans les pages de propriétés de votre projet.  
  
 `/** */`  
 Séparateurs multilignes.  
  
 Il existe des règles de mise en forme à suivre quand vous utilisez les délimiteurs `/** */`.  
  
-   Sur la ligne qui contient le délimiteur `/**`, si le reste de la ligne n’est constitué que d’espace blanc, la ligne n’est pas traitée pour les commentaires. Si le premier caractère après le délimiteur `/**` est un espace blanc, celui-ci est ignoré et le reste de la ligne est traité. Sinon, tout le texte de la ligne après le délimiteur `/**` est traité comme faisant partie du commentaire.  
  
-   Sur la ligne qui contient le délimiteur `*/`, s’il n’y a que des espaces blancs jusqu’au délimiteur `*/`, cette ligne est ignorée. Sinon, le texte de la ligne jusqu’au délimiteur `*/` est traité comme faisant partie du commentaire, conformément aux règles de critères spéciaux décrites dans la puce suivante.  
  
-   Pour les lignes situées après celle qui commence par le délimiteur `/**`, le compilateur recherche un modèle commun au début de chaque ligne. Le modèle peut se composer d’un espace blanc facultatif et d’un astérisque (`*`), suivi d’autres espaces blancs facultatifs. Si le compilateur détecte un modèle commun au début de chaque ligne qui ne commence pas par le délimiteur `/**` ou `*/`, il ignore ce modèle pour chaque ligne.  
  
 Les exemples suivants illustrent ces règles.  
  
-   La seule partie du commentaire suivant qui sera traitée est la ligne qui commence par `<summary>`. Les trois formats de balise produisent les mêmes commentaires.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Le compilateur identifie un modèle commun « * » au début des deuxième et troisième lignes. Le modèle n’est pas inclus dans la sortie.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Le compilateur ne détecte aucun modèle commun dans le commentaire suivant, car le deuxième caractère sur la troisième ligne n’est pas un astérisque. Ainsi, tout le texte des deuxième et troisième lignes est traité comme faisant partie du commentaire.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Le compilateur ne détecte aucun modèle dans le commentaire suivant pour deux raisons. Tout d’abord, le nombre d’espaces avant l’astérisque n’est pas cohérent. Ensuite, la cinquième ligne commence par une tabulation, qui ne correspond pas à des espaces. Ainsi, tout le texte des lignes deux à cinq est traité comme faisant partie du commentaire.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Commentaires sur la documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [/doc (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Commentaires sur la documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

