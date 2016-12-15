---
title: "Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39; contenant la classe de base &#39;&lt;nom_classe&gt;&#39; est requise | Microsoft Docs"
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
  - "bc30007"
  - "vbc30007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30007"
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39; contenant la classe de base &#39;&lt;nom_classe&gt;&#39; est requise
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une référence à l’assembly '\<nom\_assembly\>' contenant la classe de base '\<nom\_classe\>' est requise. Ajoutez\-en une à votre projet.  
  
 La classe est définie dans une bibliothèque de liens dynamiques \(DLL\) ou un assembly qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] nécessite une référence pour éviter toute ambiguïté au cas où la classe serait définie dans plusieurs DLL ou assemblys.  
  
 **ID d’erreur :** BC30007  
  
### Pour corriger cette erreur  
  
-   Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.  
  
## Voir aussi  
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)   
 [Dépannage de références rompues](/visual-studio/ide/troubleshooting-broken-references)