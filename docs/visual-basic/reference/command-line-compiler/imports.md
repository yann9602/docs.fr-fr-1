---
title: /Imports (Visual Basic) | Documents Microsoft
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
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
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
ms.openlocfilehash: 1dcbba442413dba63aef31fd40a511bad5e8217b
ms.lasthandoff: 03/13/2017

---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
Importe des espaces de noms à partir d’un assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`namespaceList`|Obligatoire. Liste délimitée par des virgules des espaces de noms à importer.|  
  
## <a name="remarks"></a>Remarques  
 La `/imports` option importe un espace de noms défini dans l’ensemble des fichiers source ou à partir de tout assembly référencé actuel.  
  
 Les membres d’un espace de noms spécifiés avec `/imports` sont disponibles pour tous les fichiers de code source dans la compilation. Utilisez le [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) à utiliser un espace de noms dans un fichier de code source unique.  
  
|Pour définir /Imports dans l’environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur le **références** onglet.<br />3.  Entrez le nom de l’espace de noms dans la zone en regard de la **ajouter une importation utilisateur** bouton.<br />4.  Cliquez sur le **ajouter une importation utilisateur** bouton.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile si `/imports:system` est spécifié.  
  
 [!code-vb[VbVbalrCompiler n °&21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
