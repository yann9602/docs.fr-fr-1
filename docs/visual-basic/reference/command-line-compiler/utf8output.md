---
title: "/utf8output (Visual Basic) | Microsoft Docs"
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
  - "-utf8output compiler option [Visual Basic]"
  - "utf8output compiler option [Visual Basic]"
  - "/utf8output compiler option [Visual Basic]"
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /utf8output (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Affiche le résultat de la compilation dans le format d'encodage UTF\-8.  
  
## Syntaxe  
  
```  
/utf8output[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Facultatif.  La valeur par défaut de cette option est `/utf8output-`, ce qui signifie que les résultats de la compilation n'utilisent pas l'encodage UTF\-8.  Les options `/utf8output` et `/utf8output+` sont équivalentes.  
  
## Notes  
 Dans certaines configurations internationales, les résultats de la compilation ne peuvent pas être affichés correctement dans la console.  Le cas échéant, utilisez `/utf8output` et redirigez la sortie du compilateur vers un fichier.  
  
> [!NOTE]
>  L'option `/utf8output` n'est pas accessible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `In.vb` et affiche la sortie du compilateur dans le format d'encodage UTF\-8.  
  
```  
vbc /utf8output in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)