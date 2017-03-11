---
title: "/imports (Visual Basic) | Microsoft Docs"
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
  - "/imports compiler option [Visual Basic]"
  - "imports compiler option [Visual Basic]"
  - "-imports compiler option [Visual Basic]"
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /imports (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Importe un espace de noms à partir d'un assembly spécifié.  
  
## Syntaxe  
  
```  
/imports:namespaceList  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`namespaceList`|Obligatoire.  Liste d'espaces de noms délimitée par des virgules à importer.|  
  
## Notes  
 L'option `/imports` permet d'importer n'importe quel espace de noms défini dans l'ensemble de fichiers sources en cours ou à partir de tout assembly référencé.  
  
 Les membres d'un espace de noms spécifiés avec `/imports` sont disponibles pour tous les fichiers de code source de la compilation.  Utilisez [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour utiliser un espace de noms dans un fichier de source de code unique.  
  
||  
|-|  
|Pour définir \/imports dans l'environnement de développement intégré Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Références**.<br />3.  Entrez le nom de l'espace de noms dans la zone située à côté du bouton **Ajouter une importation utilisateur**.<br />4.  Cliquez sur le bouton **Ajouter une importation utilisateur**.|  
  
## Exemple  
 Le code suivant compile si `/imports:system` est spécifié :  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/imports_1.vb)]  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)