---
title: "/langversion (C# Compiler Options) | Microsoft Docs"
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
  - "/langversion"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/langversion compiler option [C#]"
  - "-langversion compiler option [C#]"
  - "langversion compiler option [C#]"
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
caps.handback.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /langversion (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Force le compilateur à accepter uniquement la syntaxe incluse dans la spécification du langage C\# choisie.  
  
## Syntaxe  
  
```  
/langversion:option  
```  
  
## Arguments  
 `option`  
 Les valeurs suivantes sont valides :  
  
|Option|Signification|  
|------------|-------------------|  
|default|Le compilateur accepte toutes les syntaxes valides des langages.|  
|ISO\-1|Le compilateur accepte uniquement la syntaxe incluse dans la spécification du langage C\# ISO\/IEC 23270:2003.|  
|ISO\-2|Le compilateur accepte uniquement la syntaxe incluse dans la spécification du langage C\# ISO\/IEC 23270:2006.  Cette spécification est disponible sur [ISO](http://go.microsoft.com/fwlink/?LinkId=144406) le site Web.|  
|3|Le compilateur accepte uniquement les syntaxes incluses dans la version 3.0 de la [Spécification du langage C\#](../../../csharp/language-reference/language-specification.md).|  
  
## Notes  
 Les métadonnées référencées par votre application C\# ne sont pas soumises à l'option de compilateur **\/langversion**.  
  
 Comme chaque version du compilateur C\# contient des extensions à la spécification du langage, **\/langversion** ne vous fournit pas les fonctionnalités équivalentes d'une version antérieure du compilateur.  
  
 Indépendamment du paramètre **\/langversion** que vous utilisez, vous utiliserez la version actuelle du common language runtime pour créer votre fichier .exe ou .dll.  Une exception est constituée par les assemblys friend et [\/moduleassemblyname \(Specify Friend Assembly for Module\)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), qui fonctionnent sous **\/langversion:ISO\-1**.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancé**.  
  
4.  Modifiez la propriété **Version du langage**.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Spécification du langage C\#](../../../csharp/language-reference/language-specification.md)