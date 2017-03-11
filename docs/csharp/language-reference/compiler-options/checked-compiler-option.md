---
title: "/checked (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "checked compiler option [C#]"
  - "-checked compiler option [C#]"
  - "/checked compiler option [C#]"
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# /checked (C# Compiler Options)
L'option **\/checked** spécifie si une instruction arithmétique sur des entiers avec un résultat d'une valeur en dehors de la place du type de données et qui est non incluse dans la portée des mots clés [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md) provoque une exception runtime.  
  
## Syntaxe  
  
```  
/checked[+ | -]  
```  
  
## Notes  
 Une instruction arithmétique sur des entiers incluse dans la portée d'un mot clé `checked` ou `unchecked` n'est pas affectée par l'option **\/checked**.  
  
 Si une instruction arithmétique sur des entiers non incluse dans la portée des mots clés `checked` ou `unchecked` donne un résultat en dehors des valeurs autorisées pour le type de données et que **\/checked\+** \(**\/checked**\) est utilisé dans la compilation, cette instruction provoquera une exception au moment de l'exécution.  Si **\/checked\-** est utilisé dans la compilation, cette même instruction ne provoquera pas d'exception au moment de l'exécution.  
  
 La valeur par défaut de cette option est **\/checked\-**.  Un scénario d'utilisation de **\/checked\-** consiste à générer de grandes applications.  Les outils automatisés sont parfois utilisés pour générer de telles applications, et ce genre d'outil peut automatiquement définir **\/checked** sur \+.  Pour remplacer la configuration globale par défaut de l'outil, spécifiez **\/checked\-**.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  Pour plus d'informations, consultez [Générer, page du Concepteur de projets \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp).  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancé**.  
  
4.  Modifiez la propriété **Vérifier les dépassements de capacité arithmétiques positifs et négatifs**.  
  
 Pour accéder par programme à cette option du compilateur, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## Exemple  
 La commande suivante compile `t2.cs`.  L'utilisation de `/checked` dans la commande spécifie que toute instruction arithmétique sur des entiers dans le fichier qui n'est pas dans la portée d'un mot clé `checked` ou `unchecked`, et qui donne un résultat en dehors des valeurs autorisées pour le type de données provoque une exception au moment de l'exécution.  
  
```  
csc t2.cs /checked  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7)