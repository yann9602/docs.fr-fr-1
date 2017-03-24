---
title: "&lt;message&gt; cette erreur peut résulter de la combinaison d’une référence de fichier avec une référence de projet à l’assembly &quot;&lt;assemblyname&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
dev_langs:
- VB
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
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
ms.openlocfilehash: a1806fd078fc05d966c718841e5b78c1323a43c2
ms.lasthandoff: 03/13/2017

---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;message&gt; cette erreur peut résulter de la combinaison d’une référence de fichier avec une référence de projet à l’assembly '&lt;assemblyname&gt;»
\<message > cette erreur peut résulter de la combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<assemblyname >. Dans ce cas, essayez de remplacer la référence de fichier pour '\<assemblyfilename >' projet '\<projectname1 >' avec une référence de projet à '\<projectname2 >'.  
  
 Code de votre projet accède à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas la [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur à résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30971  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB Guide pratique pour ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB Comment : modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Dépannage de références rompues](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)
