---
title: "/reference (Visual Basic) | Microsoft Docs"
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
  - "/reference compiler option [Visual Basic]"
  - "r compiler option [Visual Basic]"
  - "-reference compiler option [Visual Basic]"
  - "/r compiler option [Visual Basic]"
  - "reference compiler option [Visual Basic]"
  - "-r compiler option [Visual Basic]"
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Entraîne le compilateur à donner des informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## Syntaxe  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`fileList`|Obligatoire.  Liste délimitée par des virgules de noms de fichiers d'assembly.  Si le nom de fichier contient un espace, mettez le nom entre guillemets.|  
  
## Notes  
 Le ou les fichiers que vous importez doivent comprendre des métadonnées de l'assembly.  Seuls les types publics sont visibles à l'extérieur de l'assembly.  L'option [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) importe des métadonnées à partir d'un module.  
  
 En cas de référence à un assembly \(Assembly A\) faisant lui\-même référence à un autre assembly \(Assembly B\), vous devez référencer Assembly B si :  
  
-   Un type utilisé à partir de l'assembly A hérite d'un type ou implémente une interface à partir de l'assembly B.  
  
-   Un champ, une propriété, un événement ou une méthode dont le type de retour ou de paramètre est issu de l'assembly B est appelé.  
  
 Utilisez l'option [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs de vos références d'assembly.  
  
 Pour que le compilateur reconnaisse un type dans un assembly \(pas dans un module\), il doit être forcé de résoudre le type.  Pour cela, vous pouvez, par exemple, définir une instance du type.  D'autres méthodes permettent au compilateur de résoudre les noms de types dans un assembly.  Par exemple, si vous héritez d'un type dans un assembly, le compilateur reconnaît ensuite le nom de type.  
  
 Le fichier réponse Vbc.rsp, qui référence les assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] couramment utilisés, est utilisé par défaut.  Utilisez `/noconfig` si vous ne voulez pas que le compilateur utilise Vbc.rsp.  
  
 La forme abrégée de `/reference`  est `/r`.  
  
## Exemple  
 Le code suivant compile le fichier source l`nput.vb` et fait référence à des assemblys issus de M`etad1.dll` et M`etad2.dll` pour produire O`ut.exe` :  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)