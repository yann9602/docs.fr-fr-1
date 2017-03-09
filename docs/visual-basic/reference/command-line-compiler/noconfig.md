---
title: "/noconfig | Microsoft Docs"
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
  - "noconfig compiler option [Visual Basic]"
  - "-noconfig compiler option [Visual Basic]"
  - "/noconfig compiler option [Visual Basic]"
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /noconfig
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie que le compilateur ne doit pas référencer automatiquement les assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] communément utilisés ou importer les espaces de noms `System` et `Microsoft.VisualBasic`.  
  
## Syntaxe  
  
```  
/noconfig  
```  
  
## Notes  
 L'option `/noconfig` indique au compilateur de ne pas compiler à l'aide du fichier Vbc.rsp qui se situe dans le même répertoire que le fichier Vbc.exe.  Le fichier Vbc.rsp référence les assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] couramment utilisés et importe les espaces de noms `System` et `Microsoft.VisualBasic`.  Le compilateur référence implicitement l'assembly System.dll à moins que l'option `/nostdlib` soit spécifiée.  L'option `/nostdlib` indique au compilateur de ne pas compiler à l'aide du fichier Vbc.rsp ou de référencer automatiquement l'assembly System.dll.  
  
> [!NOTE]
>  Les assemblys Mscorlib.dll et Microsoft.VisualBasic.dll sont toujours référencés.  
  
 Vous pouvez modifier le fichier Vbc.rsp pour spécifier des options du compilateur supplémentaires qui doivent être incluses dans chaque compilation Vbc.exe \(sauf en cas de spécification de l'option `/noconfig`\).  Pour plus d'informations, consultez [@ \(Specify Response File\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Le compilateur traite les dernières options passées à la commande `vbc`.  En conséquence, toute option incluse sur la ligne de commande substitue la définition de la même option dans le fichier Vbc.rsp.  
  
> [!NOTE]
>  L'option `/noconfig` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Voir aussi  
 [\/nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ \(Specify Response File\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)