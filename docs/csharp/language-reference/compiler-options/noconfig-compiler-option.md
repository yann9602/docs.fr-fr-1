---
title: "/noconfig (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/noconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/noconfig compiler option [C#]"
  - "csc.rsp"
  - "-noconfig compiler option [C#]"
  - "noconfig compiler option [C#]"
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# /noconfig (C# Compiler Options)
L'option **\/noconfig** indique au compilateur de ne pas compiler à l'aide du fichier csc.rsp, qui se trouve dans le même répertoire que le fichier csc.exe et est chargé à partir de celui\-ci.  
  
## Syntaxe  
  
```  
/noconfig  
```  
  
## Notes  
 Le fichier csc.rsp référence tous les assemblys qui accompagnent le .NET Framework.  Les références réelles que l'environnement de développement Visual Studio .NET inclut dépendent du type de projet.  
  
 Vous pouvez modifier le fichier csc.rsp et spécifier des options de compilation supplémentaires à inclure dans chaque compilation exécutée à partir de la ligne de commande à l'aide de csc.exe \(à l'exception de l'option **\/noconfig**\).  
  
 Le compilateur traite les dernières options passées à la commande **csc**.  En conséquence, toute option incluse sur la ligne de commande substitue le paramétrage de la même option dans le fichier csc.rsp.  
  
 Si vous voulez éviter que le compilateur recherche et utilise les paramètres répertoriés dans le fichier csc.rsp, spécifiez l'option **\/noconfig**.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)