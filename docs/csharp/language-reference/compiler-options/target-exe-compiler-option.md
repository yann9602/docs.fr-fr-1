---
title: "/target:exe (C# Compiler Options) | Microsoft Docs"
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
  - "/exe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#], /target:exe"
  - "/target compiler options [C#], /target:exe"
  - "-target compiler options [C#], /target:exe"
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:exe (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Avec l'option **\/target:exe**, le compilateur crée une application console exécutable \(EXE\).  
  
## Syntaxe  
  
```  
/target:exe  
```  
  
## Notes  
 L'option **\/target:exe** est activée par défaut.  Le fichier exécutable est créé avec l'extension .exe.  
  
 Utilisez l'option [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) pour créer un exécutable de programme Windows.  
  
 Sauf si vous spécifiez l'option [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), le nom du fichier de sortie prend le nom du fichier d'entrée contenant la méthode [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md).  
  
 Tous les fichiers spécifiés sur la ligne de commande avant l'option **\/out** ou **\/target:module** suivante sont utilisés pour créer le fichier .exe.  
  
 Une seule méthode **Main** est requise dans les fichiers de code source qui sont compilés en un fichier .exe.  L'option du compilateur [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) vous permet de spécifier la classe contenant la méthode **Main** lorsque votre code possède plusieurs classes contenant une méthode **Main**.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Type de sortie**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemple  
 Chacune des lignes de commande suivantes compile `in.cs` et crée le fichier `in.exe` :  
  
```  
csc /target:exe in.cs  
csc in.cs  
```  
  
## Voir aussi  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)