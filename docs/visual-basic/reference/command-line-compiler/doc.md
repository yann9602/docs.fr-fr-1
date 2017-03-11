---
title: "/doc | Microsoft Docs"
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
  - "doc compiler option [Visual Basic]"
  - "-doc compiler option [Visual Basic]"
  - "/doc compiler option [Visual Basic]"
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /doc
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Traite les commentaires de documentation pour les diriger vers un fichier XML.  
  
## Syntaxe  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`+`  &#124; `-`|Facultatif.  Si vous spécifiez \+, ou simplement `/doc`, le compilateur générera des informations de documentation et les placera dans un fichier XML.  La spécification de `-`  revient à ne pas spécifier `/doc` ; ainsi, aucune information de documentation n'est créée.|  
|`file`|Requis si `/doc:` est utilisé.  Spécifie le fichier de sortie XML, qui est rempli avec les commentaires extraits des fichiers de code source de la compilation.  Si le nom de fichier contient un espace, placez\-le entre guillemets \(" "\).|  
  
## Notes  
 L'option `/doc` contrôle si le compilateur génère un fichier XML contenant des commentaires de documentation.  Si vous utilisez la syntaxe `/doc:``file`, le paramètre `file` spécifie le nom du fichier XML.  Si vous utilisez `/doc` ou `/doc+`, le compilateur tire le nom du fichier XML à partir du fichier exécutable ou de la bibliothèque que le compilateur crée.  Si vous utilisez `/doc-` ou que vous ne spécifiez pas l'option `/doc`, le compilateur ne crée pas de fichier XML.  
  
 Dans les fichiers de code source, les commentaires de documentation peuvent précéder les définitions suivantes :  
  
-   Types définis par l'utilisateur, tels qu'une [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou une [interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Des membres, tels qu'un champ, un [événement](../../../visual-basic/language-reference/statements/event-statement.md), une [propriété](../../../visual-basic/language-reference/statements/property-statement.md), une [fonction](../../../visual-basic/language-reference/statements/function-statement.md) ou une [sous\-routine](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Pour utiliser le fichier XML généré avec la fonctionnalité [IntelliSense](/visual-studio/ide/using-intellisense) de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)], autorisez le nom du fichier XML à être identique à celui de l'assembly que vous souhaitez prendre en charge.  Assurez\-vous que le fichier XML est dans le même répertoire que l'assembly afin que le fichier .xml soit également recherché lorsque l'assembly est référencé dans le projet [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  Les fichiers de documentation XML ne sont pas requis pour qu'IntelliSense fonctionne pour le code dans un projet ou dans des projets référencés par un projet.  
  
 À moins que vous compiliez avec `/target:module`, le fichier XML contient les balises `<assembly></assembly>`.  Ces balises spécifient le nom du fichier contenant le manifeste d'assembly pour le fichier de sortie de la compilation.  
  
 Consultez [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) pour savoir comment générer la documentation à partir de commentaires dans votre code.  
  
||  
|-|  
|Pour définir \/doc dans l'environnement de développement intégré de Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Définissez la valeur dans la zone **Générer le fichier de documentation XML**.|  
  
## Exemple  
 Consultez [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) pour obtenir un exemple.  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)