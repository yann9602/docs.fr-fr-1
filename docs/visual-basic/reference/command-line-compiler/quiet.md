---
title: "/quiet | Microsoft Docs"
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
  - "/quiet"
  - "quiet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-quiet compiler option [Visual Basic]"
  - "/quiet compiler option [Visual Basic]"
  - "quiet compiler option [Visual Basic]"
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /quiet
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Empêche le compilateur d'afficher du code pour des erreurs et des avertissements liés à la syntaxe.  
  
## Syntaxe  
  
```  
/quiet  
```  
  
## Notes  
 Par défaut, `/quiet` n'est pas activée.  Lorsque le compilateur signale une erreur ou un avertissement lié à la syntaxe, il renvoie également la ligne du code source.  Pour les applications qui analysent les résultats de la compilation, il est parfois plus pratique que le compilateur exporte uniquement le texte du diagnostic.  
  
 Dans l'exemple suivant, `Module1` extrait une erreur qui inclut le code source compilé sans `/quiet`.  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Sortie :  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 Lorsque ce code est compilé avec `/quiet`, le compilateur extrait uniquement ce qui suit :  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  L'option `/quiet` n'est pas accessible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `T2.vb` et n'affiche pas de code pour les diagnostics du compilateur liés à la syntaxe :  
  
```  
vbc /quiet t2.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)