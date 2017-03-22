---
title: "Génération à partir de la ligne de commande (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 49f84c221e18457ab46534ca46da7c4764a8ee40
ms.lasthandoff: 03/13/2017

---
# <a name="building-from-the-command-line-visual-basic"></a>Génération à partir de la ligne de commande (Visual Basic)
Un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet se compose d’un ou plusieurs fichiers source séparés. Pendant le processus appelé compilation, ces fichiers sont regroupés en un seul package, un seul fichier exécutable qui peut être exécuté en tant qu’application.  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit un compilateur de ligne de commande comme alternative aux programmes de compilation dans le [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE). Le compilateur de ligne de commande est conçu pour les situations dans lesquelles vous nécessitent l’ensemble des fonctionnalités de l’IDE, par exemple, lorsque vous êtes à l’aide ou écriture pour les ordinateurs avec un espace mémoire ou stockage limitées sur le système.  
  
 Lors de la compilation à partir de la ligne de commande, vous devez explicitement référencer Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] bibliothèque d’exécution via la `/reference` option du compilateur.  
  
 Pour compiler des fichiers sources à partir la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, choisissez le **générer** commande à partir de la **Build** menu.  
  
> [!TIP]
>  Lorsque vous générez des fichiers de projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur les **vbc** commande et ses commutateurs dans la fenêtre Sortie. Pour afficher ces informations, ouvrez le [boîte de dialogue Options, projets et Solutions, générer et exécuter](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez la **niveau de détail de sortie de génération du projet MSBuild** à **Normal** ou un niveau supérieur de détail. Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
 Vous pouvez compiler des fichiers projet (.vbproj) à une invite de commandes à l’aide de MSBuild. Pour plus d’informations, consultez [référence de ligne de commande](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) et [procédure pas à pas : utilisation de MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : appeler le compilateur de ligne de commande](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Décrit comment appeler le compilateur de ligne de commande à l’invite de commandes MS-DOS ou à partir d’un sous-répertoire spécifique.  
  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Fournit une liste d’exemples de lignes de commande que vous pouvez modifier pour votre usage personnel.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 Fournit des listes d’options du compilateur, organisées par ordre alphabétique ou par objet.  
  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Décrit comment compiler des sections de code.  
  
 [Génération et nettoyage de solutions et de projets dans Visual Studio](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Explique comment organiser ce qui figureront dans les différentes générations, choisir les propriétés du projet et vous assurer que les projets sont générés dans l’ordre correct.
