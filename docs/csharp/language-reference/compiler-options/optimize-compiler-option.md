---
title: "/optimize (C# Compiler Options) | Microsoft Docs"
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
  - "/optimize"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/optimize compiler option [C#]"
  - "-o compiler option [C#]"
  - "optimize compiler option [C#]"
  - "/o compiler option [C#]"
  - "-optimize compiler option [C#]"
  - "compiler optimization [C#]"
  - "o compiler option [C#]"
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /optimize (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/optimize** active ou désactive les optimisations effectuées par le compilateur pour rendre votre fichier de sortie plus compact, plus rapide et plus efficace.  
  
## Syntaxe  
  
```  
/optimize[+ | -]  
```  
  
## Notes  
 L'option **\/optimize** indique aussi au Common Language Runtime d'optimiser le code au moment de l'exécution.  
  
 Par défaut, les optimisations sont désactivées.  Spécifiez **\/optimize\+** pour activer les optimisations.  
  
 Lorsque vous générez un module destiné à être utilisé par un assembly, utilisez les mêmes paramètres **\/optimize** que ceux de l'assembly.  
  
 **\/o** est la forme abrégée de **\/optimize**.  
  
 Vous pouvez combiner les options **\/optimize** et [\/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Optimiser le code**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## Exemple  
 Compilez `t2.cs`et activer les optimisations du compilateur :  
  
```  
csc t2.cs /optimize  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)