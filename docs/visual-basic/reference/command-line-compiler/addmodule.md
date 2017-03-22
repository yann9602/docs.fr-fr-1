---
title: /addmodule | Documents Microsoft
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
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 949962905ec933dc42301bf8c21654e73dbe2f70
ms.lasthandoff: 03/13/2017

---
# <a name="addmodule"></a>/addmodule
Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Obligatoire. Liste délimitée par des virgules des fichiers qui contiennent des métadonnées, mais ne contiennent pas de manifestes d’assembly. Les noms de fichier contenant des espaces doivent être entourés de guillemets (« »).  
  
## <a name="remarks"></a>Remarques  
 Les fichiers répertoriés par le `fileList` paramètre doit être créé avec la `/target:module` option, ou avec l’équivalent d’un autre compilateur `/target:module`.  
  
 Tous les modules ajoutés avec `/addmodule` doit être dans le même répertoire que le fichier de sortie au moment de l’exécution. Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit être dans le répertoire de l’application en cours d’exécution. Si elle n’est pas le cas, vous obtenez un <xref:System.TypeLoadException>erreur.</xref:System.TypeLoadException>  
  
 Si vous spécifiez (implicitement ou explicitement) n’importe quel[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option autre que `/target:module` avec `/addmodule`, les fichiers que vous transmettez à `/addmodule` font partie de l’assembly du projet. Un assembly est requis pour exécuter un fichier de sortie qui contient un ou plusieurs fichiers ajoutés avec `/addmodule`.  
  
 Utilisez [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pour importer des métadonnées à partir d’un fichier qui contient un assembly.  
  
> [!NOTE]
>  La `/addmodule` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant crée un module.  
  
 [!code-vb[VbVbalrCompiler&#47;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Le code suivant importe les types du module.  
  
 [!code-vb[VbVbalrCompiler&#48;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Lorsque vous exécutez `t1`, il renvoie `802`.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
