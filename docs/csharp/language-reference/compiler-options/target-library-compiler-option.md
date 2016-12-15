---
title: "/target:library (C# Compiler Options) | Microsoft Docs"
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
  - "/dll"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:library"
  - "target compiler options [C#], /target:library"
  - "/target compiler options [C#], /target:library"
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:library (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Avec l'option **\/target:library**, le compilateur crée une DLL au lieu d'un fichier exécutable \(EXE\).  
  
## Syntaxe  
  
```  
/target:library  
```  
  
## Notes  
 La DLL est créée avec l'extension .dll.  
  
 À moins que vous ne spécifiiez un autre nom avec l'option [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), le fichier de sortie adopte le nom du premier fichier d'entrée.  
  
 Tous les fichiers spécifiés sur la ligne de commande avant l'option **\/out** ou **\/target:module** suivante sont utilisés pour créer le fichier .dll.  
  
 Lors de la génération d'un fichier .dll, une méthode [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) n'est pas obligatoire.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Type de sortie**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemple  
 Compilez `in.cs` et créez le fichier `in.dll` :  
  
```  
csc /target:library in.cs  
```  
  
## Voir aussi  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)