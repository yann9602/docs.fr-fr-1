---
title: "/debug (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/debug"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "debug compiler option [C#]"
  - "-debug compiler option [C#]"
  - "/debug compiler option [C#]"
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /debug (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Si vous spécifiez l'option **\/debug**, le compilateur génère des informations de débogage et les stocke dans le ou les fichiers de sortie.  
  
## Syntaxe  
  
```  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## Arguments  
 `+` &#124; `-`  
 Si vous spécifiez `+` ou simplement **\/debug**, le compilateur générera des informations de débogage et les placera dans une base de données du programme \(fichier .pdb\).  Si vous spécifiez `-`, qui est appliqué si vous ne spécifiez pas **\/debug**, aucune information de débogage n'est créée.  
  
 `full` &#124; `pdbonly`  
 Spécifie le type d'informations de débogage générées par le compilateur.  Si vous spécifiez l'argument full ou si vous ne spécifiez pas **\/debug:pdbonly**, un débogueur sera attaché au programme en cours d'exécution.  La spécification de pdbonly permet un débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche du code en langage assembleur uniquement lorsque le programme en cours d'exécution est attaché au débogueur.  
  
## Notes  
 Utilisez cette option pour créer des générations de débogage.  Si vous ne spécifiez pas **\/debug**, **\/debug\+** ou **\/debug:full**, vous ne pourrez pas déboguer le fichier de sortie de votre programme.  
  
 Si vous utilisez **\/debug:full**, sachez qu'il existe un impact sur la vitesse et sur la taille de code optimisé JIT, ainsi qu'un faible impact sur la qualité du code en cas d'utilisation de **\/debug:full**.  Nous recommandons l'utilisation de **\/debug:pdbonly** ou d'aucun PDB pour la génération du code de version finale.  
  
> [!NOTE]
>  Une différence entre **\/debug:pdbonly** et **\/debug:full** est qu'avec **\/debug:full** le compilateur émet un <xref:System.Diagnostics.DebuggableAttribute>, qui est utilisé pour indiquer au compilateur JIT que les informations de débogage sont disponibles.  Par conséquent, vous obtiendrez une erreur si votre code contient le jeu <xref:System.Diagnostics.DebuggableAttribute> défini à la valeur false si vous utilisez **\/debug:full**.  
  
 Pour plus d'informations sur la configuration des performances de débogage d'une application, consultez [Simplification du débogage d'une image](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  
  
 Pour modifier l'emplacement du fichier .pdb, consultez [\/pdb \(Specify Debug Symbol File\)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancé**.  
  
4.  Modifiez la propriété **Infos de débogage**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## Exemple  
 Placez des informations de débogage dans le fichier de sortie `app.pdb` :  
  
```  
csc /debug /pdb:app.pdb test.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)