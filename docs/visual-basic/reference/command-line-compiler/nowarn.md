---
title: "/nowarn | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nowarn compiler option [Visual Basic]"
  - "/nowarn compiler option [Visual Basic]"
  - "-nowarn compiler option [Visual Basic]"
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /nowarn
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Désactive la fonction du compilateur permettant de générer des avertissements.  
  
## Syntaxe  
  
```  
/nowarn[:numberList]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`numberList`|Facultatif.  Liste délimitée par des virgules des numéros d'ID d'avertissement que le compilateur doit supprimer.  Si les ID d'avertissement ne sont pas spécifiés, tous les avertissements sont supprimés.|  
  
## Notes  
 L'option `/nowarn` a pour conséquence que le compilateur ne génère pas d'avertissement.  Pour supprimer un avertissement, fournissez l'ID d'avertissement à l'option `/nowarn` qui suit les deux\-points.  Séparez les numéros des avertissements par une virgule.  
  
 Il suffit de spécifier la partie numérique de l'identificateur de l'avertissement.  Par exemple, si vous souhaitez supprimer BC42024, numéro d'avertissement pour les variables locales inutilisées, spécifiez `/nowarn:42024`.  
  
 Pour plus d'informations sur les numéros d'ID d'avertissement, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
||  
|-|  
|Pour définir \/nowarn dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Activez la case à cocher **Désactiver tous les avertissements** pour désactiver tous les avertissements.<br />     \- ou \-<br />     Pour désactiver un avertissement particulier, cliquez sur **Aucun** dans la liste déroulante adjacente à l'avertissement.|  
  
## Exemple  
 Le code suivant compile `T2.vb` et n'affiche pas d'avertissements.  
  
```  
vbc /nowarn t2.vb  
```  
  
## Exemple  
 Le code suivant compile `T2.vb` et n'affiche pas d'avertissements pour les variables locales inutilisées \(42024\).  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic)