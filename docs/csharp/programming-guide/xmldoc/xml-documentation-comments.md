---
title: "Commentaires de documentation XML (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.xml"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, commentaires de code XML"
  - "fichiers de code source C#"
  - "commentaires (C#), XML"
  - "commentaires de documentation (C#)"
  - "XML (C#), commentaires de code"
  - "commentaires de documentation XML (C#)"
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Commentaires de documentation XML (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dans Visual C \#, vous pouvez créer de la documentation de votre code en incluant des éléments XML dans des champs de commentaire spéciaux \(indiqués par trois barres obliques\) dans le code source, juste avant le bloc de code auquel les commentaires font référence, par exemple :  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 Lorsque vous utilisez l'option [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour compiler, le compilateur recherche toutes les balises XML dans le code source et crée un fichier de documentation XML.  Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061).  
  
 Pour faire référence à des éléments XML \(par exemple, votre fonction traite des éléments XML spécifiques que vous souhaitez décrire dans un commentaire de documentation XML\), vous pouvez utiliser le mécanisme de citation standard \(`<` et `>`\).  Pour faire référence aux identificateurs génériques dans les éléments de référence de code \(`cref`\), vous pouvez utiliser des caractères d'échappement \(par exemple, `cref=”List&;lt;T>”`\) ou des accolades \(`cref=”List{T}”`\).  En tant que cas particulier, le compilateur analyse les accolades comme des crochets pointus pour rendre le commentaire de documentation moins fastidieux à créer lorsqu'il s'agit de faire référence aux identificateurs génériques.  
  
> [!NOTE]
>  Les commentaires de documentation XML ne sont pas des métadonnées. Ils ne sont pas inclus dans l'assembly compilé et ne sont donc pas accessibles par réflexion.  
  
## Dans cette section  
  
-   [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [Traitement du fichier XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [Délimiteurs pour les balises de documentation](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [Procédure : utiliser les fonctionnalités de la documentation XML](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## Rubriques connexes  
 Pour plus d'informations, consultez :  
  
-   [\/doc \(Traiter les commentaires de documentation\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)