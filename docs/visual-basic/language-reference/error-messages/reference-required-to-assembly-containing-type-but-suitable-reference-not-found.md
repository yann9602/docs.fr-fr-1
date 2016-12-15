---
title: "Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39; contenant le type &#39;&lt;nom_type&gt;&#39; est requise, mais une r&#233;f&#233;rence appropri&#233;e n’a pas &#233;t&#233; trouv&#233;e en raison de l’ambig&#252;it&#233; entre les projets &#39;&lt;nom_projet1&gt;&#39; et &#39;&lt;nom_projet2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30969"
  - "vbc30969"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30969"
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39; contenant le type &#39;&lt;nom_type&gt;&#39; est requise, mais une r&#233;f&#233;rence appropri&#233;e n’a pas &#233;t&#233; trouv&#233;e en raison de l’ambig&#252;it&#233; entre les projets &#39;&lt;nom_projet1&gt;&#39; et &#39;&lt;nom_projet2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, qui est défini en dehors de votre projet. Cependant, des références de projet désignent plusieurs assemblys définissant ce type.  
  
 Les projets cités produisent des assemblys de même nom. Par conséquent, le compilateur ne peut pas déterminer quel assembly utiliser pour le type auquel vous accédez.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30969  
  
### Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans vos propriétés de projet, ajoutez une référence au fichier contenant l’assembly qui définit le type que vous utilisez.  
  
## Voir aussi  
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Dépannage de références rompues](/visual-studio/ide/troubleshooting-broken-references)