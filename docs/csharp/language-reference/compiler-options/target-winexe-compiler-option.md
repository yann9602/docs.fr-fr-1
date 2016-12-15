---
title: "/target:winexe (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/target:winexe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/target compiler options [C#], /target:winexe"
  - "-target compiler options [C#], /target:winexe"
  - "target compiler options [C#], /target:winexe"
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:winexe (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Avec l'option **\/target:winexe**, le compilateur crée un programme Windows exécutable \(EXE\).  
  
## Syntaxe  
  
```  
/target:winexe  
```  
  
## Notes  
 Le fichier exécutable est créé avec l'extension .exe.  Un programme Windows est un programme qui fournit une interface utilisateur à partir de la bibliothèque du .NET Framework ou avec les API Win32.  
  
 Utilisez l'option [\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) pour créer une application console.  
  
 Sauf si vous spécifiez l'option [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), le nom du fichier de sortie prend le nom du fichier d'entrée contenant la méthode [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md).  
  
 Tous les fichiers spécifiés sur la ligne de commande avant l'option **\/out** ou [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) suivante sont utilisés pour créer le programme Windows.  
  
 Une seule méthode **Main** est requise dans les fichiers de code source qui sont compilés en un fichier .exe.  L'option du compilateur [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) vous permet de spécifier la classe qui contient la méthode **Main** lorsque votre code possède plusieurs classes contenant une méthode **Main**.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Type de sortie**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemple  
 Compilez `in.cs` en un programme Windows :  
  
```  
csc /target:winexe in.cs  
```  
  
## Voir aussi  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)