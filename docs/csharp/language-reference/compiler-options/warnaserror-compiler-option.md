---
title: "/warnaserror (C# Compiler Options) | Microsoft Docs"
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
  - "/warnaserror"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/warnaserror compiler option [C#]"
  - "-warnaserror compiler option [C#]"
  - "warnaserror compiler option [C#]"
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warnaserror (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Avec l'option **\/warnaserror\+**, tous les avertissements sont considérés comme des erreurs.  
  
## Syntaxe  
  
```  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## Notes  
 Les messages affichés habituellement comme des avertissements sont indiqués en tant qu'erreurs, et le processus de génération est arrêté \(aucun fichier de sortie n'est généré\).  
  
 L'option **\/warnaserror\-** est activée par défaut et, dès lors, les avertissements n'empêchent pas la génération d'un fichier de sortie.  Si vous utilisez **\/warnaserror**, qui est identique à **\/warnaserror\+**, les avertissements sont considérés comme des erreurs.  
  
 Si vous souhaitez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules répertoriant les numéros d'avertissement à traiter comme des erreurs.  
  
 Utilisez l'option [\/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) pour spécifier le niveau des avertissements affichés par le compilateur.  Utilisez l'option [\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) pour désactiver certains avertissements.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Considérer les avertissements comme des erreurs**.  
  
     Pour définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>  
  
## Exemple  
 Compilez `in.cs` et indiquez au compilateur de ne pas afficher les avertissements :  
  
```  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)