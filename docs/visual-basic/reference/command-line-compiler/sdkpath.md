---
title: "/sdkpath | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sdkpath"
  - "/sdkpath"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-sdkpath compiler option [Visual Basic]"
  - "/sdkpath compiler option [Visual Basic]"
  - "sdkpath compiler option [Visual Basic]"
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /sdkpath
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie l'emplacement de Mscorlib.dll et Microsoft.VisualBasic.dll.  
  
## Syntaxe  
  
```  
/sdkpath:path  
```  
  
## Arguments  
 `path`  
 Répertoire contenant les versions de Mscorlib.dll et de Microsoft.VisualBasic.dll à utiliser pour la compilation.  Ce chemin d'accès n'est pas vérifié tant qu'il n'est pas chargé.  Mettez le nom de répertoire entre guillemets \(" "\) s'il contient un espace.  
  
## Notes  
 Cette option demande au compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de charger les fichiers Mscorlib.dll et Microsoft.VisualBasic.dll à partir d'un emplacement autre que celui utilisé par défaut.  L'option `/sdkpath`  a été conçue pour être utilisée avec [\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).  [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] utilise différentes versions de ces bibliothèques d'assistance pour éviter l'utilisation de types et de fonctionnalités de langue introuvables sur les appareils.  
  
> [!NOTE]
>  L'option `/sdkpath` n'est pas accessible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  L'option `/sdkpath` est définie lorsqu'un projet Smart Device [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est chargé.  
  
 Pour indiquer au compilateur de compiler sans référence à la bibliothèque Visual Basic Runtime, utilisez l'option `/vbruntime`.  Pour plus d'informations, consultez [\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## Exemple  
 Le code suivant compile `Myfile.vb` avec [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], à l'aide des versions de Mscorlib.dll et Microsoft.VisualBasic.dll trouvées dans le répertoire d'installation  [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] par défaut, situé sur le lecteur C.  En général, il est préférable d'utiliser la version la plus récente de [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)   
 [\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)