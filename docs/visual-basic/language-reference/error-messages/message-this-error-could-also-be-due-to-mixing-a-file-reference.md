---
title: "&lt;message&gt; cette erreur peut résulter également une référence de fichier avec une référence de projet à l’assembly &#39;&lt; AssemblyName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30e5d5aca09e7b74e16dd05cdc0c5c361c1657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;message&gt; cette erreur peut résulter également une référence de fichier avec une référence de projet à l’assembly &#39;&lt; AssemblyName&gt;&#39;
\<message > Cette erreur peut résulter également une référence de fichier avec une référence de projet à l’assembly '\<assemblyname >. Dans ce cas, essayez de remplacer la référence de fichier pour '\<nom_fichier_assembly >' dans le projet '\<nom_projet1 >' avec une référence de projet à '\<nom_projet2 >'.  
  
 Le code de votre projet permet d’accéder à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] à résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30971  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)  
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)  
 [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)
