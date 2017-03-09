---
title: "/rootnamespace | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/rootnamespace"
  - "rootnamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/rootnamespace compiler option [Visual Basic]"
  - "-rootnamespace compiler option [Visual Basic]"
  - "rootnamespace compiler option [Visual Basic]"
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# /rootnamespace
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie un espace de noms pour toutes les déclarations de type.  
  
## Syntaxe  
  
```  
/rootnamespace:namespace  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`namespace`|Nom de l'espace de noms dans lequel vous voulez inclure toutes les déclarations de type pour le projet en cours.|  
  
## Notes  
 Si vous utilisez le fichier exécutable Visual Studio \(Devenv.exe\) pour compiler un projet créé dans l'environnement de développement intégré Visual Studio, utilisez `/rootnamespace` pour spécifier la valeur de la propriété <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>.  Consultez [Commutateurs de la ligne de commande de Devenv](/visual-studio/ide/reference/devenv-command-line-switches) pour plus d'informations.  
  
 Utilisez le désassembleur MSIL du common language runtime \(I`ldasm.exe`\) pour afficher les noms d'espaces de noms dans votre fichier de sortie.  
  
||  
|-|  
|Pour définir\/référencer dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Application**.<br />3.  Modifiez la valeur dans la zone **Espace de noms racine**.|  
  
## Exemple  
 Le code suivant compile `In.vb` et place toutes les déclarations de type dans l'espace de noms `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Ildasm.exe \(IL Disassembler\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)