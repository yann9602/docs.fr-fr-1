---
title: "@ (Specify Response File) (Visual Basic) | Microsoft Docs"
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
  - "@ (Specify Response File) compiler option [Visual Basic]"
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# @ (Specify Response File) (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie un fichier qui comprend les options du compilateur et les fichiers de code source à compiler.  
  
## Syntaxe  
  
```  
@response_file  
```  
  
## Arguments  
 `response_file`  
 Obligatoire.  Fichier qui répertorie les options du compilateur ou les fichiers de code source à compiler.  Mettez le nom de fichier entre guillemets \(" "\) s'il contient un espace.  
  
## Notes  
 Le compilateur traite les options du compilateur et les fichiers de code source spécifiés dans un fichier réponse de la même façon que s'ils avaient été spécifiés dans la ligne de commande.  
  
 Pour spécifier plusieurs fichiers réponse dans une compilation, spécifiez plusieurs options de fichier réponse, telles que dans les exemples suivants.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Dans un fichier réponse, plusieurs options du compilateur et fichiers de code source peuvent figurer sur une même ligne.  En revanche, si vous spécifiez une seule option du compilateur, celle\-ci doit obligatoirement figurer sur une seule et même ligne.  Les fichiers réponse peuvent contenir des commentaires, précédés du symbole `#`.  
  
 Vous pouvez combiner des options spécifiées dans la ligne de commande à des options spécifiées dans un ou plusieurs fichiers réponse.  Le compilateur traite les options de commande au fur et à mesure.  Par conséquent, des arguments de ligne de commande peuvent substituer des options précédemment affichées dans les fichiers réponse.  Inversement, les options d'un fichier réponse substituent les options affichées précédemment dans la ligne de commande ou dans d'autres fichiers réponse.  
  
 Visual Basic fournit le fichier Vbc.rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe.  Le fichier Vbc.rsp est inclus par défaut, à moins que l'option `/noconfig` soit utilisée.  Pour plus d'informations, consultez [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  L'option `@` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Voici quelques lignes extraites d'un exemple de fichier réponse :  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'option `@` avec le fichier réponse nommé `File1.rsp`.  
  
```  
vbc @file1.rsp  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)