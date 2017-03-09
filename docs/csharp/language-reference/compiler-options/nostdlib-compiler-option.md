---
title: "/nostdlib (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nostdlib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nostdlib compiler option [C#]"
  - "-nostdlib compiler option [C#]"
  - "/nostdlib compiler option [C#]"
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# /nostdlib (C# Compiler Options)
**\/nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.  
  
## Syntaxe  
  
```  
/nostdlib[+ | -]  
```  
  
## Notes  
 Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.  
  
 Si vous ne spécifiez pas **\/nostdlib**, mscorlib.dll est importé dans votre programme \(ce qui équivaut à spécifier **\/nostdlib\-**\). Les options **\/nostdlib** et **\/nostdlib\+** sont équivalentes.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancées**.  
  
4.  Modifiez la propriété **Ne pas référencer mscorlib.dll**.  
  
 Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)