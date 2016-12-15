---
title: "/nostdlib (Visual Basic) | Microsoft Docs"
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
  - "nostdlib compiler option [Visual Basic]"
  - "-nostdlib compiler option [Visual Basic]"
  - "/nostdlib compiler option [Visual Basic]"
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nostdlib (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Empêche le compilateur de référencer automatiquement les bibliothèques standard.  
  
## Syntaxe  
  
```  
/nostdlib  
```  
  
## Notes  
 L'option `/nostdlib` supprime la référence automatique à l'assembly System.dll et empêche le compilateur de lire le fichier Vbc.rsp.  Le fichier Vbc.rsp, situé dans le même répertoire que le fichier  Vbc.exe file, références les assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] communément utilisés et importe les espaces de noms `System` et `Microsoft.VisualBasic`.  
  
> [!NOTE]
>  Les assemblys Mscorlib.dll et Microsoft.VisualBasic.dll sont toujours référencés.  
  
> [!NOTE]
>  L'option `/nostdlib` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `T2.vb` sans référencer les bibliothèques standard.  Vous devez définir la constante de compilation conditionnelle `_MYTYPE` à la valeur de chaîne "Empty" pour supprimer l'objet `My`.  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## Voir aussi  
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)