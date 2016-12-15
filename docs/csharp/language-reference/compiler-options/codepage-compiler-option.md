---
title: "/codepage (C# Compiler Options) | Microsoft Docs"
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
  - "/codepage"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/codepage compiler option [C#]"
  - "codepage compiler option [C#]"
  - "-codepage compiler option [C#]"
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /codepage (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette option spécifie la page de codes à utiliser pendant la compilation si la page requise n'est pas la page de codes courante par défaut pour le système.  
  
## Syntaxe  
  
```  
/codepage:id  
```  
  
## Arguments  
 `id`  
 est l'identificateur d'une page de codes à utiliser pour tous les fichiers de code source de la compilation.  
  
## Notes  
 Si vous compilez un ou plusieurs fichiers de code source n'ayant pas été créés pour utiliser la page de codes par défaut de votre ordinateur, vous pouvez utiliser l'option **\/codepage** pour spécifier la page de codes à utiliser.  **\/codepage** s'applique à tous les fichiers de code source inclus dans la compilation.  
  
 L'utilisation de l'option **\/codepage** n'est pas nécessaire si les fichiers de code source ont été créés avec la page de codes par défaut utilisée sur votre ordinateur ou bien avec un format de codage UNICODE ou UTF\-8.  
  
 Consultez [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) pour plus d'informations sur la façon de vous procurer les pages de codes sont prises en charge sur votre système.  
  
 Cette option du compilateur n'est pas disponible dans Visual Studio et ne peut pas être modifiée par programme.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)