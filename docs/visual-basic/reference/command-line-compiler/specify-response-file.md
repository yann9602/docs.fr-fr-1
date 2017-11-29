---
title: "@ (spécifier un fichier réponse) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ced258713983ded06fa70cb65d56071b41cdc75b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-specify-response-file-visual-basic"></a>@ (spécifier un fichier réponse) (Visual Basic)
Spécifie un fichier qui contient les options du compilateur et les fichiers de code source à compiler.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Arguments  
 `response_file`  
 Obligatoire. Un fichier qui répertorie les options du compilateur ou les fichiers de code source à compiler. Placez le nom de fichier entre guillemets ( » «) si elle contient un espace.  
  
## <a name="remarks"></a>Remarques  
 Le compilateur traite les options du compilateur et les fichiers de code source spécifiés dans un fichier réponse comme s’ils avaient été spécifiés sur la ligne de commande.  
  
 Pour spécifier plusieurs fichiers réponse dans une compilation, spécifiez plusieurs options de fichier de réponse, telles que les éléments suivants.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Dans une réponse du fichier, plusieurs options du compilateur et les fichiers de code source peuvent apparaître sur une seule ligne. Une spécification de l’option du compilateur unique doit apparaître sur une seule ligne (ne peut pas étendre sur plusieurs lignes). Fichiers réponse peuvent contenir des commentaires qui commencent par le `#` symbole.  
  
 Vous pouvez combiner des options spécifiées sur la ligne de commande avec les options spécifiées dans un ou plusieurs fichiers de réponse. Le compilateur traite les options de commande qu’il les rencontre. Par conséquent, les arguments de ligne de commande peuvent remplacer des options précédemment affichées dans les fichiers réponse. À l’inverse, les options dans un fichier réponse remplacent les options répertoriées précédemment sur la ligne de commande ou dans d’autres fichiers réponse.  
  
 Visual Basic fournit le fichier Vbc.rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe. Le fichier Vbc.rsp est inclus par défaut, à moins que le `/noconfig` option est utilisée. Pour plus d’informations, consultez [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  Le `@` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Les lignes suivantes sont à partir d’un exemple de fichier de réponse.  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `@` option avec le fichier de réponse nommé `File1.rsp`.  
  
```  
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
