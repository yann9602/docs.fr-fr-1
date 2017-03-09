---
title: "/help, /? (Visual Basic) | Microsoft Docs"
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
  - "/? compiler option [Visual Basic]"
  - "-help compiler option [Visual Basic]"
  - "/help compiler option [Visual Basic]"
  - "help compiler option [Visual Basic]"
  - "-? compiler option [Visual Basic]"
  - "? compiler option [Visual Basic]"
ms.assetid: eb984aa5-ac98-4d0b-a0d2-24238d7bc8dc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# /help, /? (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Affiche les options du compilateur.  
  
## Syntaxe  
  
```  
/help  
' -or-  
/?  
```  
  
## Notes  
 Si cette option est incluse dans une compilation, aucun fichier de sortie n'est créé et aucune compilation ne se produit.  
  
> [!NOTE]
>  L'option `/help` n'est pas accessible dans l'environnement de développement [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)]. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant affiche l'aide à partir de la ligne de commande.  
  
```  
vbc /help  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)