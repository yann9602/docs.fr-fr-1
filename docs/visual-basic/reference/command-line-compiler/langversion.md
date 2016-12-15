---
title: "/langversion (Visual Basic) | Microsoft Docs"
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
  - "/langversion compiler option [Visual Basic]"
  - "langversion compiler option [Visual Basic]"
  - "-langversion compiler option [Visual Basic]"
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /langversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Entraîne le compilateur à accepter uniquement la syntaxe incluse dans la version de langage Visual Basic spécifiée.  
  
## Syntaxe  
  
```  
/langversion:version  
```  
  
## Arguments  
 `version`  
 Obligatoire.  Version de langage à utiliser pendant la compilation.  Les valeurs acceptées sont `9`, `9.0`, `10` et `10.0`.  
  
## Notes  
 L'option `/langversion` spécifie la syntaxe acceptée par le compilateur.  Par exemple, si vous spécifiez que la version de langage est 9.0, le compilateur génère des erreurs pour la syntaxe uniquement valide dans la version 10.0 et les versions ultérieures.  
  
 Vous pouvez utiliser cette option lorsque vous développez des applications destinées à différentes versions du .NET Framework.  Par exemple, si vous les destinez à .NET Framework 3.5, vous pouvez utiliser cette option pour garantir que vous n'utilisez pas la syntaxe de la version de langage 10.0.  
  
 Vous pouvez définir directement `/langversion` uniquement à l'aide de la ligne de commande.  Pour plus d'informations, consultez [Cibler une version spécifique du .NET Framework](/visual-studio/ide/targeting-a-specific-dotnet-framework-version).  
  
## Exemple  
 Le code suivant compile `sample.vb` pour Visual Basic 9.0.  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Cibler une version spécifique du .NET Framework](/visual-studio/ide/targeting-a-specific-dotnet-framework-version)