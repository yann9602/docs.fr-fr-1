---
title: "#ExternalSource Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#Externalsource"
  - "#ExternalSource"
  - "vb.ExternalSource"
  - "Externalsource"
  - "vb.#ExternalSource"
  - "ExternalSource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ExternalSource directive (#ExternalSource)"
  - "#ExternalSource directive"
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: 160
caps.handback.revision: 160
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #ExternalSource Directive
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indique un mappage entre les lignes spécifiques du code source et le texte extérieur à la source.  
  
## Syntaxe  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## Composants  
 `StringLiteral`  
 Le chemin d'accès à la source externe.  
  
 `IntLiteral`  
 Le numéro de la première ligne de la source externe.  
  
 `LogicalLine`  
 La ligne de la source externe à laquelle l'erreur s'est produite.  
  
 `#End ExternalSource`  
 Met fin au bloc `#ExternalSource`.  
  
## Notes  
 Cette directive n'est utilisée que par le compilateur et le débogueur.  
  
 Un fichier source peut inclure des directives de source externe, qui indiquent un mappage entre les lignes spécifiques de code dans le fichier source et le texte externe à la source, tel qu'un fichier .aspx.  Si des erreurs sont rencontrées dans le code source désigné lors de la compilation, elles sont identifiées comme émanant de la source externe.  
  
 Ces directives de source externe n'ont aucun effet sur la compilation et ne peuvent pas être imbriquées.  Elles sont réservées à une utilisation interne par l'application.  
  
## Voir aussi  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)