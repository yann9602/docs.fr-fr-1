---
title: "/libpath | Microsoft Docs"
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
  - "libpath compiler option [Visual Basic]"
  - "/libpath compiler option [Visual Basic]"
  - "-libpath compiler option [Visual Basic]"
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /libpath
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie l'emplacement des assemblys référencés.  
  
## Syntaxe  
  
```  
/libpath:dirList  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`dirList`|Obligatoire.  Liste délimitée par des points\-virgules des répertoires où le compilateur doit vérifier si un assembly référencé ne se trouve pas dans le répertoire de travail actif \(répertoire depuis lequel vous appelez le compilateur\) ou dans le répertoire système du Common Language Runtime.  Si le nom de répertoire contient un espace, placez\-le entre guillemets \(" "\).|  
  
## Notes  
 L'option `/libpath` spécifie l'emplacement des assemblys référencés par l'option [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md).  
  
 Le compilateur recherche les références d'assembly qui ne sont pas complètement qualifiées dans l'ordre suivant :  
  
1.  Répertoire de travail en cours.  Il s'agit du répertoire à partir duquel le compilateur est appelé.  
  
2.  Répertoire système du Common Language Runtime.  
  
3.  Répertoires spécifiés par `/libpath`.  
  
4.  Répertoires spécifiés par la variable d'environnement LIB.  
  
 L'option  `/libpath` peut être cumulée ; si vous la spécifiez plus d'une fois, elle sera ajoutée aux valeurs précédentes.  
  
 Utilisez l'option `/reference` pour spécifier une référence d'assembly.  
  
||  
|-|  
|Pour définir \/libpath dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Références**.<br />3.  Cliquez sur le bouton **Chemins d'accès des références...**.<br />4.  Dans la boîte de dialogue **Chemins d'accès des références**, entrez le nom du répertoire dans la zone **Dossier :**.<br />5.  Cliquez sur **Ajouter un dossier**.|  
  
## Exemple  
 Le code suivant compile `T2.vb` pour créer un fichier .exe.  Le compilateur recherche les références d'assembly dans le répertoire de travail, dans le répertoire racine du lecteur C: et dans le répertoire New Assemblies du lecteur C:.  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## Voir aussi  
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)