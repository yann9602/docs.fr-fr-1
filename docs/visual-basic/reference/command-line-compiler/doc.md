---
title: /doc | Documents Microsoft
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
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
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
ms.openlocfilehash: 1054eb256eb7670ee0454b02fc094e0306c1218d
ms.lasthandoff: 03/13/2017

---
# <a name="doc"></a>/doc
Traite les commentaires de documentation pour les diriger vers un fichier XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. Spécification +, ou simplement `/doc`, le compilateur génère des informations de documentation et placez-le dans un fichier XML. Spécification de `-` équivaut à ne pas spécifier `/doc`, aucune information de documentation doit être créé à l’origine.|  
|`file`|Obligatoire si l'option `/doc:` est utilisée. Spécifie le fichier XML de sortie, qui est rempli avec les commentaires à partir des fichiers de code source de la compilation. Si le nom de fichier contient un espace, placez le nom entre guillemets (« »).|  
  
## <a name="remarks"></a>Remarques  
 La `/doc` option contrôle si le compilateur génère un fichier XML contenant les commentaires de documentation. Si vous utilisez la `/doc:``file` syntaxe, le `file` paramètre spécifie le nom du fichier XML. Si vous utilisez `/doc` ou `/doc+`, le compilateur prend le nom du fichier XML à partir du fichier exécutable ou une bibliothèque que le compilateur crée. Si vous utilisez `/doc-` ou ne spécifiez pas la `/doc` option, le compilateur ne crée pas un fichier XML.  
  
 Dans les fichiers de code source, les commentaires de documentation peuvent précéder les définitions suivantes :  
  
-   Défini par l’utilisateur types, tels qu’un [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Membres, tel qu’un champ, [événement](../../../visual-basic/language-reference/statements/event-statement.md), [propriété](../../../visual-basic/language-reference/statements/property-statement.md), [fonction](../../../visual-basic/language-reference/statements/function-statement.md), ou [sous-routine](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Pour utiliser le fichier XML généré avec la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense) fonctionnalité, soit le nom de fichier du fichier XML de la même que l’assembly que vous souhaitez prendre en charge. Assurez-vous que le fichier XML est dans le même répertoire que l’assembly afin que lorsque l’assembly est référencé dans le [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] projet, le fichier .xml est trouvé aussi. Fichiers de documentation XML ne sont pas requis pour qu’IntelliSense fonctionne pour le code dans un projet ou dans des projets référencés par un projet.  
  
 Sauf si vous compilez avec `/target:module`, le fichier XML contient les balises `<assembly></assembly>`. Ces balises spécifient le nom du fichier contenant le manifeste d’assembly pour le fichier de sortie de la compilation.  
  
 Consultez la page [balises de commentaire XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) pour savoir comment générer la documentation à partir de commentaires dans votre code.  
  
|Pour définir /doc dans Visual Studio environnement de développement intégré|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Définissez la valeur de la **fichier de documentation XML générer** boîte.|  
  
## <a name="example"></a>Exemple  
 Consultez la page [documenter votre Code avec XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) pour obtenir un exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Documentation de votre code avec le langage XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
