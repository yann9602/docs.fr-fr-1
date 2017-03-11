---
title: "/keyfile | Microsoft Docs"
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
  - "/keyfile compiler option [Visual Basic]"
  - "keyfile compiler option [Visual Basic]"
  - "-keyfile compiler option [Visual Basic]"
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /keyfile
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie un fichier contenant une clé ou une paire de clés afin d'attribuer un nom fort à un assembly.  
  
## Syntaxe  
  
```  
/keyfile:file  
```  
  
## Arguments  
 `file`  
 Obligatoire.  Le fichier qui comprend la clé.  Si le nom de fichier contient un espace, mettez le nom entre guillemets \(" "\).  
  
## Notes  
 Le compilateur insère la clé publique dans le manifeste de l'assembly et signe ensuite l'assembly final avec la clé privée.  Pour générer un fichier de clé, tapez `sn -k file` sur la ligne de commande.  Pour plus d'informations, consultez [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
 Si vous compilez à l'aide de `/target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l'assembly qui est créé lorsque vous compilez un assembly à l'aide de [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  Utilisez [\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous souhaitez obtenir un assembly partiellement signé.  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé \(<xref:System.Reflection.AssemblyKeyFileAttribute>\) dans le code source de n'importe quel module Microsoft Intermediate Language.  
  
 Si `/keyfile` et [\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) sont tous deux spécifiés \(par une option de ligne de commande ou par un attribut personnalisé\) dans la même compilation, le compilateur essaie d'abord le conteneur de clé.  Si cette tentative aboutit, l'assembly est signé avec les informations figurant dans le conteneur de clé.  Si le compilateur ne trouve pas le conteneur de clé, il essaie le fichier spécifié avec `/keyfile`.  Si cette tentative réussit, l'assembly est signé avec les informations du fichier de clé et les informations de clé sont installées dans le conteneur de clé \(résultat similaire à celui de `sn -i`\) afin que, lors de la prochaine compilation, le conteneur de clé soit valide.  
  
 Notez qu'un fichier de clé pourrait contenir uniquement la clé publique.  
  
 Pour plus d'informations sur la signature d'un assembly, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
> [!NOTE]
>  L'option `/keyfile` n'est pas accessible dans l'environnement de développement [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)]. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile le fichier source `Input.vb` et spécifie un fichier de clé.  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## Voir aussi  
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)