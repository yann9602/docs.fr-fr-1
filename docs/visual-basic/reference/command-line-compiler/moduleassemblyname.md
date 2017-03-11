---
title: "/moduleassemblyname | Microsoft Docs"
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
  - "moduleassemblyname compiler option [Visual Basic]"
  - "/moduleassemblyname compiler option [Visual Basic]"
  - "-moduleassemblyname compiler option [Visual Basic]"
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /moduleassemblyname
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie le nom de l'assembly dont ce module fera partie.  
  
## Syntaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`assembly_name`|Nom de l'assembly dont ce module fera partie.|  
  
## Notes  
 Le compilateur traite l'option `/moduleassemblyname` uniquement si l'option `/target:module` a été spécifiée.  Le compilateur crée alors un module.  Le module créé par le compilateur est valide uniquement pour l'assembly spécifié avec l'option `/moduleassemblyname`.  Si vous placez le module dans un assembly différent, des erreurs d'exécution se produiront.  
  
 L'option `/moduleassemblyname` est exigée uniquement lorsque les conditions suivantes se vérifient :  
  
-   Un type de données dans le module doit disposer d'un accès à un type `Friend` dans un assembly référencé.  
  
-   L'assembly référencé a accordé l'accès d'assembly friend à l'assembly dans lequel le module sera généré.  
  
 Pour plus d'informations sur la création de module, consultez [\/target](../../../visual-basic/reference/command-line-compiler/target.md).  Pour plus d'informations sur les assemblys friend, consultez [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
> [!NOTE]
>  L'option `/moduleassemblyname` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir d'une invite de commande.  
  
## Voir aussi  
 [Comment : générer un assembly multifichier](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)