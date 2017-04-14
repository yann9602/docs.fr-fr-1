---
title: "G&#233;n&#233;ration et compilation de code source dynamique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèle CodeDOM (Code Document Object Model)"
  - "CodeDOM"
  - "modélisation de code source indépendante du langage"
  - "langages, prise en charge de plusieurs langages par CodeDOM"
  - "langages multiples pris en charge par CodeDOM"
  - "code source dans plusieurs langages"
  - "System.CodeDOM (espace de noms)"
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# G&#233;n&#233;ration et compilation de code source dynamique
Le Kit de développement .NET Framework SDK inclut un mécanisme appelé CodeDOM \(Code Document Object Model\) qui permet aux développeurs de générer un code source dans plusieurs langages de programmation au moment de l'exécution, en fonction d'un seul modèle qui représente le code à rendre.  
  
 Pour représenter le code source, les éléments CodeDOM sont reliés les uns aux autres pour former une structure de données désignée par graphique CodeDOM qui modélise la structure d'un code source.  
  
 L'espace de noms `System.CodeDom` définit les types qui peuvent représenter la structure logique du code source, indépendamment de tout langage de programmation.  L'espace de noms `System.CodeDom.Compiler` définit les types pour la génération de code source à partir des graphiques CodeDOM et la gestion de la compilation du code source dans les langages pris en charge.  Les fournisseurs de compilateurs ou les développeurs peuvent étendre le jeu des langages pris en charge.  
  
 La modélisation de code source indépendante du langage peut s'avérer précieuse lorsqu'un programme a besoin de générer du code source pour un modèle de programme dans plusieurs langages ou pour un langage cible indéterminé.  Par exemple, certains concepteurs utilisent le CodeDOM comme une interface d'abstraction de langage afin de produire du code source dans le langage de programmation approprié, à condition que la prise en charge CodeDOM de ce langage soit disponible.  
  
 Le .NET Framework inclut des générateurs et des compilateurs de code pour [C\#](frlrfMicrosoftCSharpCSharpCodeProviderClassTopic), [JScript](frlrfMicrosoftJScriptJScriptCodeProviderClassTopic) et [Visual Basic](frlrfMicrosoftVisualBasicVBCodeProviderClassTopic).  
  
## Dans cette section  
 [Utilisation du CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 Décrit les usages courants du CodeDOM et illustre la génération d'un graphique d'objets simple à l'aide du CodeDOM.  
  
 [Génération du code source et compilation d'un programme à partir d'un graphique CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 Décrit comment générer du code source et compiler le code généré avec un compilateur externe à l'aide de classes définies dans l'espace de noms `System.CodeDom.Compiler`.  
  
 [Comment : créer un fichier de documentation XML à l'aide de CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 Décrit comment utiliser CodeDOM pour générer du code avec des commentaires de documentation XML et compiler le code généré afin qu'il crée la sortie de documentation XML.  
  
 [Comment : créer une classe à l'aide de CodeDOM](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 Décrit comment utiliser CodeDOM pour générer une classe contenant des champs, des propriétés, une méthode, un constructeur et un point d'entrée.  
  
## Référence  
 <xref:System.CodeDom>  
 Définit les éléments qui représentent les éléments de code dans les langages de programmation qui ciblent le Common Language Runtime.  
  
 <xref:System.CodeDom.Compiler>  
 Définit les interfaces de génération et de compilation du code au moment de l'exécution.  
  
## Rubriques connexes  
 [CodeDOM Quick Reference](http://msdn.microsoft.com/fr-fr/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 Fournit aux développeurs une méthode pour trouver rapidement des éléments CodeDOM qui représentent des éléments du code source.