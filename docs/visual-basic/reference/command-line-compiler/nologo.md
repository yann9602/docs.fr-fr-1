---
title: "/nologo (Visual Basic) | Microsoft Docs"
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
  - "-nologo compiler option [Visual Basic]"
  - "banners, suppressing startup"
  - "nologo compiler option [Visual Basic]"
  - "/nologo compiler option [Visual Basic]"
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /nologo (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Supprime l'affichage de la page de copyright et des messages d'informations lors de la compilation.  
  
## Syntaxe  
  
```  
/nologo  
```  
  
## Notes  
 Si vous spécifiez `/nologo`, le compilateur n'affiche pas la page de copyright.  Par défaut, l'option `/nologo` n'est pas activée.  
  
> [!NOTE]
>  L'option `/nologo` n'est pas disponible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `T2.vb` et n'affiche pas de bannière de copyright.  
  
```  
vbc /nologo t2.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)