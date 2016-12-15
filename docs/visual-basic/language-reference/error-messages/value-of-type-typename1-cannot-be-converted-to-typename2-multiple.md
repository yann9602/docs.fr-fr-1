---
title: "Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30961"
  - "bc30961"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30961"
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La valeur de type '\<NomType1\>' ne peut pas être convertie en '\<NomType2\>'.L'incompatibilité de type peut résulter de la combinaison d'une référence de fichier pour '\<CheminFichier1\>' dans le projet '\<NomProjet1\>' et d'une référence de fichier pour '\<CheminFichier2\>' dans le projet '\<NomProjet2\>'Si les deux assemblys sont identiques, essayez de remplacer ces deux références pour qu'elles se situent dans le même emplacement.  
  
 Si un projet fait plusieurs références de fichier à un assembly, le compilateur ne peut pas garantir qu'un type peut être converti en un autre.  
  
 Chaque référence de fichier spécifie un chemin d'accès et un nom pour le fichier de sortie d'un projet \(en général un fichier DLL\).  Le compilateur ne peut pas garantir que les fichiers de sortie viennent de la même source ou qu'ils représentent la même version du même assembly.  Par conséquent, il ne peut pas garantir que les types dans les références différentes sont du même type ou même que l'un peut être converti en l'autre.  
  
 Vous pouvez utiliser une référence de fichier unique si vous savez que les assemblys référencés ont la même identité d'assembly.  L'*identité d'assembly* inclut le nom de l'assembly, la version, la clé publique le cas échéant, et la culture.  Ces informations identifient de manière unique l'assembly.  
  
 **ID d'erreur :** BC30961  
  
### Pour corriger cette erreur  
  
-   Si les assemblys référencés ont la même identité d'assembly, supprimez ou remplacez l'une des références de fichier pour qu'il y ait une référence de fichier unique.  
  
-   Si les assemblys référencés n'ont pas la même identité d'assembly, modifiez votre code afin qu'il ne tente pas de convertir un type dans l'une en un type dans l'autre.  
  
## Voir aussi  
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)   
 [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)