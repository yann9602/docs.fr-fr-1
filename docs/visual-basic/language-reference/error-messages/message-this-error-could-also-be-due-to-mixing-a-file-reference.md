---
title: "&lt;message&gt; Cette erreur peut r&#233;sulter de la combinaison d’une r&#233;f&#233;rence de fichier et d’une r&#233;f&#233;rence de projet pour l’assembly &#39;&lt;nom_assembly&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30971"
  - "vbc30971"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30971"
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;message&gt; Cette erreur peut r&#233;sulter de la combinaison d’une r&#233;f&#233;rence de fichier et d’une r&#233;f&#233;rence de projet pour l’assembly &#39;&lt;nom_assembly&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

\<message\> Cette erreur peut résulter de la combinaison d’une référence de fichier et d’une référence de projet pour l’assembly '\<nom\_assembly\>'. Dans ce cas, essayez de remplacer la référence de fichier pour '\<nom\_fichier\_assembly\>' dans le projet '\<nom\_projet1\>' par une référence de projet pour '\<nom\_projet2\>'.  
  
 Le code de votre projet permet d’accéder à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] à résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30971  
  
### Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.  
  
## Voir aussi  
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Dépannage de références rompues](/visual-studio/ide/troubleshooting-broken-references)