---
title: "/recurse | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/recurse compiler option [Visual Basic]"
  - "-recurse compiler option [Visual Basic]"
  - "recurse compiler option [Visual Basic]"
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /recurse
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Compile des fichiers de code source dans tous les répertoires enfants du répertoire spécifié ou du répertoire du projet.  
  
## Syntaxe  
  
```  
/recurse:[dir\]file  
```  
  
## Arguments  
 `dir`  
 Facultatif.  Répertoire dans lequel vous voulez commencer la recherche.  Si ce répertoire n'est pas spécifié, la recherche commence dans le répertoire du projet.  
  
 `file`  
 Obligatoire.  Le ou les fichiers à rechercher.  Les caractères génériques sont autorisés.  
  
## Notes  
 Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser `/recurse`.  Si aucun nom de fichier de sortie n'est spécifié, le compilateur base le nom du fichier de sortie sur le premier fichier d'entrée traité.  Généralement, c'est le premier fichier de la liste de fichiers compilés lorsqu'ils sont affichés par ordre alphabétique.  Par conséquent, il est préférable de spécifier un fichier de sortie à l'aide de l'option `/out`.  
  
> [!NOTE]
>  L'option `/recurse` n'est pas accessible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile tous les fichiers [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dans le répertoire en cours.  
  
```  
vbc *.vb  
```  
  
 Le code suivant compile tous les fichiers [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dans le répertoire `Test\ABC` et dans tous les répertoires en dessous de celui\-ci, puis génère `Test.ABC.dll`.  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/out](../../../visual-basic/reference/command-line-compiler/out.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)