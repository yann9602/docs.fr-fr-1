---
title: Documentation XML (F#)
description: "En savoir plus sur la prise en charge en F # pour générer la documentation à partir de commentaires."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d99ab1b6-e170-4ec2-a543-43ea7ab15bb2
ms.openlocfilehash: 20768a7d4ea17c926318043f658691819a3d7d2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-documentation"></a>Documentation XML

Vous pouvez générer la documentation à trois barres obliques (/ / /) à partir de code des commentaires en F #. Commentaires XML peuvent précéder les déclarations dans les fichiers de code (.fs) ou les fichiers de signature (.fsi).


## <a name="generating-documentation-from-comments"></a>Générer la Documentation à partir de commentaires
La prise en charge en F # pour générer la documentation à partir de commentaires est le même que dans d’autres langages .NET Framework. Comme dans d’autres langages .NET Framework, le [-doc option du compilateur](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04) vous permet de générer un fichier XML qui contient des informations que vous pouvez convertir dans la documentation à l’aide d’un outil tel que Sandcastle. La documentation générée à l’aide des outils conçus pour une utilisation avec les assemblys qui sont écrits dans d’autres langages .NET Framework généralement produire une vue des API qui sont basés sur le formulaire compilé des constructions F #. À moins que les outils spécifiquement prennent en charge F #, documentation générée par ces outils ne correspond pas à la vue F # d’une API.

Pour plus d’informations sur la façon de générer la documentation à partir de XML, consultez [commentaires de Documentation XML &#40; C &#35; Guide de programmation &#41; ](https://msdn.microsoft.com/library/b2s063f7).


## <a name="recommended-tags"></a>Balises recommandées
Il existe deux façons d’écrire des commentaires de documentation XML. Une consiste à écrire la documentation directement dans un commentaire à trois barres obliques, sans l’aide de balises XML. Si vous faites cela, le texte de commentaire entier est pris comme documentation de résumé pour la construction de code qui suit immédiatement. Utilisez cette méthode lorsque vous souhaitez écrire uniquement un bref résumé pour chaque construction. L’autre méthode est d’utiliser des balises XML pour fournir une documentation plus structurée. La seconde méthode vous permet de spécifier des remarques séparées pour un bref résumé, remarques supplémentaires, la documentation pour chaque paramètre et paramètre de type et les exceptions levées et une description de la valeur de retour. Le tableau suivant décrit les balises XML qui sont reconnus dans les commentaires de code XML F #.



|Syntaxe de balise|Description|
|----------|-----------|
|**&lt;c&gt;***texte***&lt;/c&gt;**|Spécifie que *texte* est le code. Cette balise peut être utilisée par les générateurs de documentation pour afficher du texte dans une police qui est appropriée pour le code.|
|**&lt;Résumé&gt;***texte* **&lt; /summary&gt;**|Spécifie que *texte* est une brève description de l’élément de programme. La description est généralement une ou deux phrases.|
|**&lt;Remarques&gt;***texte* **&lt; /Remarques&gt;**|Spécifie que *texte* contient des informations supplémentaires sur l’élément de programme.|
|**&lt;Param nom = «***nom***»&gt;***description***&lt;/param&gt;**|Spécifie le nom et une description pour un paramètre de fonction ou une méthode.|
|**&lt;typeparam nom = «***nom***»&gt;***description***&lt;/typeparam&gt;**|Spécifie le nom et une description pour un paramètre de type.|
|**&lt;Retourne&gt;***texte* **&lt; /retourne&gt;**|Spécifie que *texte* décrit la valeur de retour d’une fonction ou une méthode.|
|**&lt;exception cref = »***type***»&gt;***description***&lt;/exception&gt;**|Spécifie le type d’exception qui peut être générée et les circonstances dans lesquelles elle est levée.|
|**&lt;Voir cref = »***référence***»&gt;***texte* **&lt; /consultez&gt;**|Spécifie un lien vers un autre élément de programme en ligne. Le *référence* est le nom tel qu’il apparaît dans le fichier de documentation XML. Le *texte* correspond au texte affiché dans le lien.|
|**&lt;seealso cref = »***référence***« /&gt;**|Spécifie un lien Voir aussi à la documentation relative à un autre type. Le *référence* est le nom tel qu’il apparaît dans le fichier de documentation XML. Voir aussi des liens s’affichent généralement en bas d’une page de documentation.|
|**&lt;Para&gt;***texte***&lt;/para&gt;**|Spécifie un paragraphe de texte. Cela permet de séparer le texte à l’intérieur de la **notes** balise.|

## <a name="example"></a>Exemple

### <a name="description"></a>Description
Voici un commentaire de documentation XML standard dans un fichier de signature.


### <a name="code"></a>Code
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]
    
## <a name="example"></a>Exemple

### <a name="description"></a>Description
L’exemple suivant montre la méthode alternative, sans les balises XML. Dans cet exemple, l’intégralité du texte dans le commentaire est considéré comme un résumé. Notez que si vous ne spécifiez pas explicitement de balise de résumé, vous ne devez pas spécifier d’autres balises, telles que **param** ou **retourne** balises.


### <a name="code"></a>Code
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]
    
## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Options du compilateur](compiler-options.md)
