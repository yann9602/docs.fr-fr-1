---
title: Commentaires de documentation XML (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.xml
dev_langs:
- CSharp
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: 26
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0762bd31ef7732ac6ed91a10aead9dca8050f862
ms.lasthandoff: 03/13/2017

---
# <a name="xml-documentation-comments-c-programming-guide"></a>Commentaires de documentation XML (Guide de programmation C#)
Dans Visual C #, vous pouvez créer de la documentation de votre code en incluant des éléments XML dans des champs de commentaire spéciaux (indiqués par trois barres obliques) dans le code source, juste avant le bloc de code auquel les commentaires font référence, par exemple :  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 Quand vous utilisez l’option [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour compiler, le compilateur recherche toutes les balises XML dans le code source et crée un fichier de documentation XML. Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061).  
  
 Pour faire référence à des éléments XML (par exemple, votre fonction traite des éléments XML spécifiques que vous souhaitez décrire dans un commentaire de documentation XML), vous pouvez utiliser le mécanisme de citation standard (`<` et `>`).  Pour faire référence aux identificateurs génériques dans les éléments de référence de code (`cref`), vous pouvez utiliser des caractères d’échappement (par exemple, `cref=”List<T>”`) ou des accolades (`cref=”List{T}”`).  En tant que cas particulier, le compilateur analyse les accolades comme des crochets pointus pour rendre le commentaire de documentation moins fastidieux à créer lorsqu'il s'agit de faire référence aux identificateurs génériques.  
  
> [!NOTE]
>  Les commentaires de documentation XML ne sont pas des métadonnées. Ils ne sont pas inclus dans l'assembly compilé et ne sont donc pas accessibles par réflexion.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [Traitement du fichier XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [Délimiteurs pour les balises de documentation](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [Procédure : utiliser les fonctionnalités de la documentation XML](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations, voir :  
  
-   [/doc (Traiter les commentaires de documentation)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)
