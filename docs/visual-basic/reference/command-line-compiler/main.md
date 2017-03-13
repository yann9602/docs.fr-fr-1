---
title: "/main | Microsoft Docs"
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
  - "main compiler option [Visual Basic]"
  - "/main compiler option [Visual Basic]"
  - "-main compiler option [Visual Basic]"
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /main
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la classe ou le module qui contient la procédure `Sub Main`.  
  
## Syntaxe  
  
```  
/main:location  
```  
  
## Arguments  
 `location`  
 Obligatoire.  Qualification complète de la classe ou du module contenant la procédure `Sub Main` à appeler au démarrage du programme.  Celle\-ci peut être sous la forme **\/main:module** ou **\/main:namespace.module**.  
  
## Notes  
 Utilisez cette option lors de la création d'un fichier exécutable ou d'un programme exécutable Windows.  Si vous omettez l'option **\/main**, le compilateur recherche une procédure `Sub Main` partagée valide dans tous les modules et toutes les classes publiques.  
  
 Consultez [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) pour obtenir des explications sur les différentes formes de la procédure `Main`.  
  
 Lorsque `location` est une classe qui hérite de <xref:System.Windows.Forms.Form>, le compilateur fournit une procédure `Main` par défaut qui démarre l'application si la classe n'a aucune procédure `Main`.  Cela vous permet de compiler le code à partir de la ligne de commande créée dans l'environnement de développement.  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### Pour définir \/main dans l'environnement de développement intégré Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Application**.  
  
3.  Vérifiez que la case à cocher **Activer l'infrastructure de l'application** n'est pas activée.  
  
4.  Modifiez la valeur dans la zone **Objet de démarrage**.  
  
## Exemple  
 Le code suivant compile `T2.vb` et `T3.vb`, en spécifiant que la procédure `Sub Main` se trouve dans la classe `Test2` :  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/fr-fr/9d030b60-e148-4366-a462-69532f02294c)   
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)