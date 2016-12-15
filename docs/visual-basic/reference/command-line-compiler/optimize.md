---
title: "/optimize | Microsoft Docs"
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
  - "optimize compiler option [Visual Basic]"
  - "/optimize compiler option [Visual Basic]"
  - "optimization, enabling"
  - "-optimize compiler option [Visual Basic]"
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optimize
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Active ou désactive les optimisations du compilateur.  
  
## Syntaxe  
  
```  
/optimize[ + | - ]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`+`  &#124; `-`|Facultatif.  L'option `/optimize-` désactive les optimisations du compilateur.  L'option `/optimize+` active les optimisations.  Par défaut, les optimisations sont désactivées.|  
  
## Notes  
 Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace.  Toutefois, les optimisations entraînant une réorganisation du code dans le fichier de sortie, la valeur `/optimize+` peut rendre le débogage difficile.  
  
 Tous les modules générés à l'aide `/target:module` pour un assembly doivent utiliser les mêmes paramètres `/optimize` que l'assembly.  Pour plus d'informations, consultez [\/target](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Vous pouvez combiner les options `/optimize` et `/debug`.  
  
||  
|-|  
|Pour définir \/optimize dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.<br />     Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Cliquez sur le bouton **Avancé**.<br />4.  Modifiez la case à cocher **Activer les optimisations**.|  
  
## Exemple  
 Le code suivant compile `T2.vb` et active les optimisations du compilateur.  
  
```  
vbc t2.vb /optimize  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)