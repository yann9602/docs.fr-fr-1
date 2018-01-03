---
title: "Référence à l’assembly &#39; requise &lt;assemblyidentity&gt;&#39; type de conteneur &#39;&lt; TypeName&gt;&#39; mais une référence appropriée n’a pas être trouvée en raison de l’ambiguïté entre les projets &#39;&lt; nom_projet1&gt;&#39; et &#39;&lt; nom_projet2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ca2454f5c306b3defd1c885dfd59ee130f3e828
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Référence à l’assembly &#39; requise &lt;assemblyidentity&gt;&#39; type de conteneur &#39;&lt; TypeName&gt;&#39; mais une référence appropriée n’a pas être trouvée en raison de l’ambiguïté entre les projets &#39;&lt; nom_projet1&gt;&#39; et &#39;&lt; nom_projet2&gt;&#39;
Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, qui est défini en dehors de votre projet. Cependant, des références de projet désignent plusieurs assemblys définissant ce type.  
  
 Les projets cités produisent des assemblys de même nom. Par conséquent, le compilateur ne peut pas déterminer quel assembly utiliser pour le type auquel vous accédez.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30969  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans vos propriétés de projet, ajoutez une référence au fichier contenant l’assembly qui définit le type que vous utilisez.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)  
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)  
 [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)
