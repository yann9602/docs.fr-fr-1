---
title: "/netcf | Microsoft Docs"
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
  - "/netcf"
  - "netcf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-netcf compiler option [Visual Basic]"
  - "netcf compiler option [Visual Basic]"
  - "/netcf compiler option [Visual Basic]"
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /netcf
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Définit le compilateur afin qu'il cible le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
## Syntaxe  
  
```  
/netcf  
```  
  
## Notes  
 L'option `/netcf` entraîne le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] à cibler le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] plutôt que le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] complet.  Les fonctionnalités de langage qui sont uniquement présentes dans le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] complet sont désactivées.  
  
 L'option `/netcf` est conçue pour être utilisée avec [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).  Les fonctionnalités de langue désactivées par `/netcf` sont les mêmes que celles qui sont absentes des fichiers ciblés avec `/sdkpath`.  
  
> [!NOTE]
>  L'option `/netcf` n'est pas accessible dans l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  L'option `/netcf` est définie lorsqu'un projet Smart Device [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est chargé.  
  
 L'option `/netcf` modifie les fonctionnalités de langue suivantes :  
  
-   Le mot clé [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md), qui met fin à l'exécution d'un programme, est désactivé.  Le programme suivant compile et exécute sans `/netcf`, mais échoue au moment de la compilation avec `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   La liaison tardive, sous quelle forme que ce soit, est désactivée.  Les erreurs de compilation sont générées lorsque des scénarios de liaison tardive sont rencontrés.  Le programme suivant compile et exécute sans `/netcf`, mais échoue au moment de la compilation avec `/netcf`.  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   Les modificateurs [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) et [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) sont désactivés.  La syntaxe de l'instruction [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) est aussi modifiée et utilise `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.  Le code suivant montre l'effet qu'exerce `/netcf` sur une compilation.  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   L'utilisation des mots clés Visual Basic 6.0 qui ont été supprimés de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur différente lorsque `/netcf` est utilisé.  Cela affecte les messages d'erreur qui apparaissent pour les mots clés suivants :  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## Exemple  
 Le code suivant compile `Myfile.vb` avec [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], à l'aide des versions de Mscorlib.dll et Microsoft.VisualBasic.dll trouvées dans le répertoire d'installation  [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] par défaut, situé sur le lecteur C.  En général, il est préférable d'utiliser la version la plus récente de [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)