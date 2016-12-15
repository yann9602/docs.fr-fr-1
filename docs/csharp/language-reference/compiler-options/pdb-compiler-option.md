---
title: "/pdb (C# Compiler Options) | Microsoft Docs"
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
  - "/pdb"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-pdb compiler option [C#]"
  - "pdb compiler option [C#]"
  - "/pdb compiler option [C#]"
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /pdb (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option du compilateur **\/pdb** spécifie le nom et l'emplacement du fichier de symboles de débogage.  
  
## Syntaxe  
  
```  
/pdb:filename  
```  
  
## Arguments  
 `filename`  
 Le nom et emplacement du fichier de symboles de débogage.  
  
## Notes  
 Lorsque vous spécifiez [\/debug \(Emit Debugging Information\)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), le compilateur crée un fichier .pdb dans le même répertoire où il crée le fichier de sortie \(.exe ou .dll\) avec un nom identique à celui du fichier de sortie.  
  
 **\/pdb** vous permet de spécifier un nom de fichier et un emplacement non définis par défaut pour le fichier .pdb.  
  
 Cette option du compilateur ne peut pas être définie dans l'environnement de développement Visual Studio, ni être modifiée par programme.  
  
## Exemple  
 Compilez `t.cs` et créez un fichier .pdb appelé tt.pdb :  
  
```  
csc /debug /pdb:tt t.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)