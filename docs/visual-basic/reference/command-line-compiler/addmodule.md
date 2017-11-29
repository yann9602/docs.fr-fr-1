---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a>/addmodule
Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Obligatoire. Délimitée par des virgules de liste de fichiers qui contiennent des métadonnées, mais ne contiennent pas de manifestes d’assembly. Les noms de fichiers contenant des espaces doivent être entourés de guillemets (« »).  
  
## <a name="remarks"></a>Remarques  
 Les fichiers répertoriés par le `fileList` paramètre doit être créé avec la `/target:module` option, ou avec l’équivalent d’un autre compilateur `/target:module`.  
  
 Tous les modules ajoutés avec `/addmodule` doivent être dans le même répertoire que le fichier de sortie au moment de l’exécution. Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit être dans le répertoire de l’application en cours d’exécution. Si elle n’est pas le cas, vous obtenez un <xref:System.TypeLoadException> erreur.  
  
 Si vous spécifiez (implicitement ou explicitement) n’importe quel[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option autre que `/target:module` avec `/addmodule`, les fichiers que vous passez à `/addmodule` font partie de l’assembly du projet. Un assembly est requis pour exécuter un fichier de sortie qui contient un ou plusieurs fichiers ajoutés avec `/addmodule`.  
  
 Utilisez [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pour importer des métadonnées à partir d’un fichier qui contient un assembly.  
  
> [!NOTE]
>  Le `/addmodule` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant crée un module.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Le code suivant importe les types du module.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Lorsque vous exécutez `t1`, elle génère `802`.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
