---
title: "/keycontainer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "-keycontainer compiler option [Visual Basic]"
  - "keycontainer compiler option [Visual Basic]"
  - "/keycontainer compiler option [Visual Basic]"
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /keycontainer
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.  
  
## Syntaxe  
  
```  
/keycontainer:container  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`container`|Obligatoire.  Fichier conteneur qui contient la clé.  Mettez le nom de fichier entre guillemets \(""\) s'il contient un espace.|  
  
## Notes  
 Le compilateur crée le composant qui peut être partagé en insérant une clé publique dans le manifeste d'assembly et en signant l'assembly final avec la clé privée.  Pour générer un fichier de clé, tapez `sn -k` `file` sur la ligne de commande.  L'option `-i`  installe la paire de clés dans un conteneur.  Pour plus d'informations, consultez [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
 Si vous compilez à l'aide de `/target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l'assembly qui est créé lorsque vous compilez un assembly à l'aide de [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé \(<xref:System.Reflection.AssemblyKeyNameAttribute>\) dans le code source de n'importe quel module MSIL \(Microsoft Intermediate Language\).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).  Utilisez [\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous souhaitez obtenir un assembly partiellement signé.  
  
 Pour plus d'informations sur la signature d'un assembly, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
> [!NOTE]
>  L'option `/keycontainer` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile le fichier source `Input.vb` et spécifie un conteneur de clés.  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## Voir aussi  
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)