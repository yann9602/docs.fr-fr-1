---
title: /main
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5bb11bc62e951339113f4b48e98e05362490ca1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="main"></a>/main
Spécifie la classe ou le module qui contient la procédure `Sub Main`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Obligatoire. Qualification complète de la classe ou le module qui contient le `Sub Main` procédure qui est appelée lorsque le programme démarre. Cela peut être sous la forme **présentée** ou **/main:namespace.module**.  
  
## <a name="remarks"></a>Notes  
 Utilisez cette option lorsque vous créez un fichier exécutable ou un programme exécutable Windows. Si le **/main** option est omise, le compilateur recherche partagé valide `Sub Main` dans tous les modules et les classes publiques.  
  
 Consultez [procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) pour en savoir plus sur les différentes formes de la `Main` procédure.  
  
 Lorsque `location` est une classe qui hérite de <xref:System.Windows.Forms.Form>, le compilateur fournit une valeur par défaut `Main` procédure qui démarre l’application si la classe n’a pas `Main` procédure. Cela vous permet de compiler du code à la ligne de commande qui a été créée dans l’environnement de développement.  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a>Pour définir l’option /main dans Visual Studio environnement de développement intégré  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
       
  
2.  Cliquez sur l’onglet **Application** .  
  
3.  Assurez-vous que le **activer l’infrastructure d’application** case à cocher n’est pas activée.  
  
4.  Modifiez la valeur dans la **objet de démarrage** boîte.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et `T3.vb`, en spécifiant que le `Sub Main` procédure se trouve dans le `Test2` classe.  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
