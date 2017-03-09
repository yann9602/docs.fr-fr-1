---
title: "D&#233;limiteurs pour les balises de documentation (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/** */ délimiteurs pour les balises de documentation C#"
  - "/// délimiteur pour les balises de documentation"
  - "XML (C#), délimiteurs"
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# D&#233;limiteurs pour les balises de documentation (Guide de programmation C#)
Pour être utilisés, les commentaires de document XML requièrent des délimiteurs, qui indiquent au compilateur où commence et se termine un commentaire de documentation.  Vous pouvez utiliser les types de délimiteurs ci\-dessous avec les balises de documentation XML :  
  
 `///`  
 Délimiteur sur une ligne.  Il s'agit de la forme illustrée dans les exemples de documentation et utilisée par les modèles de projets Visual C\#.  S'il y a un caractère espace blanc qui suit le délimiteur, ce caractère n'est pas inclus dans la sortie XML.  
  
> [!NOTE]
>  L'IDE de Visual Studio inclut une fonctionnalité appelée Édition de commentaire intelligente qui insère automatiquement les balises \<summary\> et \<\/summary\>, et place le curseur dans ces balises lorsque vous tapez le délimiteur `///` dans l'éditeur de code.  Accédez à cette fonctionnalité à partir de [Options, Éditeur de texte, C\#, Mise en forme](/visual-studio/ide/reference/options-text-editor-csharp-formatting) dans vos pages de propriétés de projet.  
  
 `/** */`  
 Séparateurs multilignes.  
  
 Il y a des règles de mise en forme à suivre lorsque vous utilisez les délimiteurs `/** */`.  
  
-   Sur la ligne qui contient le délimiteur `/**` , si le reste de la ligne correspond à un espace blanc, la ligne n'est pas traitée comme commentaire.  Si le premier caractère après le délimiteur `/**`  est un espace blanc, il est ignoré et le reste de la ligne est traité.  Sinon, tout le texte de la ligne qui suit le délimiteur `/**` est traité comme une partie du commentaire.  
  
-   Sur la ligne qui contient le délimiteur `*/` , si seul un espace blanc précède le délimiteur `*/`, la ligne est ignorée.  Sinon, le texte précédant le délimiteur `*/` sur la ligne est traité comme une partie du commentaire, sujet aux règles des critères spéciaux décrites dans le paragraphe suivant.  
  
-   Pour les lignes après celle qui commence par le délimiteur `/**`, le compilateur recherche un modèle commun au début de chaque ligne.  Le modèle peut se composer d'un espace blanc facultatif et un astérisque \(`*`\), suivis par d'autres espaces blancs facultatifs.  Si le compilateur trouve un modèle commun au début de chaque ligne qui ne commence pas par le délimiteur `/**` ou le délimiteur `*/`, il ignore ce modèle pour chaque ligne.  
  
 Les exemples suivants illustrent ces règles.  
  
-   La seule partie du commentaire suivant qui sera traitée est la ligne commençant par `<summary>`.  Les trois formats de balise produisent les mêmes commentaires.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
  
    ```  
  
-   Le compilateur identifie un modèle commun " \* " au début des deuxième et troisième lignes.  Le modèle n'est pas inclus dans la sortie.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Le compilateur ne trouve aucun modèle commun dans le commentaire suivant parce que le deuxième caractère sur la troisième ligne n'est pas un astérisque.  Par conséquent, tout le texte sur les deuxième et troisième lignes est traité en tant que commentaire.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Le compilateur ne trouve aucune séquence dans ce commentaire pour deux raisons.  En premier lieu, le nombre d'espaces avant que l'astérisque n'est pas cohérent.  D'autre part, la cinquième ligne commence par une tabulation, qui ne correspond pas à des espaces.  Par conséquent, tout le texte entre les lignes deux et cinq est traité en tant que commentaire.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Commentaires de documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Commentaires de documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)