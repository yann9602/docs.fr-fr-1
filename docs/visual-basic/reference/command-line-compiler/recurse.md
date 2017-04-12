---
title: /recurse | Documents Microsoft
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
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
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
ms.openlocfilehash: fbf7d67c7f70345e62ddbb03c8626b688b5c593b
ms.lasthandoff: 03/13/2017

---
# <a name="recurse"></a>/recurse
Compile les fichiers de code source dans tous les répertoires enfants du répertoire spécifié ou le répertoire du projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 Facultatif. Le répertoire dans lequel vous souhaitez commencer la recherche. Si non spécifié, la recherche commence dans le répertoire du projet.  
  
 `file`  
 Obligatoire. L’ou les fichiers à rechercher. Les caractères génériques sont autorisés.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser `/recurse`. Si aucun nom de fichier de sortie n’est spécifié, le compilateur base le nom de fichier de sortie sur le premier fichier d’entrée traité. Il s’agit généralement du premier fichier dans la liste des fichiers compilés lorsqu’ils sont affichés par ordre alphabétique. Pour cette raison, il est préférable de spécifier un fichier de sortie à l’aide de la `/out` option.  
  
> [!NOTE]
>  La `/recurse` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les fichiers dans le répertoire actif.  
  
```  
vbc *.vb  
```  
  
 Le code suivant compile tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de fichiers dans le `Test\ABC` répertoire et ses sous-répertoires, puis génère `Test.ABC.dll`.  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
