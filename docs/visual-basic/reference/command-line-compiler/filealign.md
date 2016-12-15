---
title: "/filealign | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "sections compiler option [Visual Basic]"
  - "alignment compiler option [Visual Basic]"
  - "-filealign compiler option [Visual Basic]"
  - "section alignment"
  - "/filealign compiler option [Visual Basic]"
  - "filealign compiler option [Visual Basic]"
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /filealign
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie l'emplacement dans lequel aligner les sections du fichier de sortie.  
  
## Syntaxe  
  
```  
/filealign:number  
```  
  
## Arguments  
 `number`  
 Obligatoire.  Valeur spécifiant l'alignement des sections du fichier de sortie.  Les valeurs valides sont 512, 1024, 2048, 4096 et 8192.  Il s'agit de valeurs en octets.  
  
## Notes  
 Vous pouvez utiliser l'option `/filealign` pour spécifier l'alignement de sections dans votre fichier de sortie.  Les sections représentent des blocs de mémoire contiguë dans un fichier exécutable portable \(PE, Portable Executable\) qui contient du code ou des données.  L'option `/filealign` vous permet de compiler votre application avec un alignement non standard ; la plupart des développeurs n'ont pas besoin de cette option.  
  
 Chaque section est alignée sur une limite qui est un multiple de la valeur `/filealign`.  Il n'y a pas de valeur par défaut fixe.  Si `/filealign` n'est pas spécifié, le compilateur sélectionne la valeur par défaut au moment de la compilation.  
  
 En spécifiant la taille de la section, vous pouvez modifier la taille du fichier de sortie.  Il est parfois utile de modifier la taille de section pour les programmes appelés à s'exécuter sur des appareils plus petits.  
  
> [!NOTE]
>  L'option `/filealign` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)