---
title: "/warn (C# Compiler Options) | Microsoft Docs"
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
  - "/warn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "warning level [C#]"
  - "/w compiler option [C#]"
  - "-w compiler option [C#]"
  - "-warn compiler option [C#]"
  - "/warn compiler option [C#]"
  - "w compiler option [C#]"
  - "warn compiler option [C#]"
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warn (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/warn** spécifie le niveau d'avertissement à afficher par le compilateur.  
  
## Syntaxe  
  
```  
/warn:option  
```  
  
## Arguments  
 `option`  
 Le niveau d'avertissement que vous souhaitez afficher pour la compilation : les chiffres peu élevés affichent uniquement les avertissements de gravité importante ; les chiffres plus élevés affichent davantage d'avertissements.  Les valeurs autorisées sont comprises entre 0 et 4 :  
  
|Niveau d'avertissement|Signification|  
|----------------------------|-------------------|  
|0|Désactive l'émission de tous les messages d'avertissement.|  
|1|Affiche les messages d'avertissement grave.|  
|2|Affiche les avertissements de niveau 1 ainsi que quelques avertissements moins graves, par exemple pour signaler le masquage de membres de classe.|  
|3|Affiche les avertissements de niveau 2 ainsi que quelques avertissements moins graves, par exemple pour signaler des expressions prenant toujours la valeur `true` ou `false`.|  
|4 \(valeur par défaut\)|Affiche tous les avertissements de niveau 3 plus les avertissements d'information.|  
  
## Notes  
 Pour obtenir des informations sur une erreur ou sur un avertissement, vous pouvez rechercher le code d'erreur dans l'index de l'aide.  Pour obtenir des informations sur une erreur ou un avertissement via d'autres méthodes, consultez [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Utilisez l'option [\/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) si vous souhaitez traiter tous les avertissements en tant qu'erreurs.  Utilisez l'option [\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) pour désactiver certains avertissements.  
  
 **\/w** est la forme abrégée de **\/warn**.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Niveau d'avertissement**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## Exemple  
 Compilez `in.cs` et indiquez au compilateur d'afficher uniquement les avertissements de niveau 1 :  
  
```  
csc /warn:1 in.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)