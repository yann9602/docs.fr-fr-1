---
title: "Array Dimensions in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dimensions, arrays"
  - "arrays [Visual Basic], dimensions"
  - "arrays [Visual Basic], rectangular"
  - "arrays [Visual Basic], rank"
  - "rectangular arrays"
  - "ranking, arrays"
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array Dimensions in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une *dimension* est une direction dans laquelle vous pouvez varier les caractéristiques des éléments d'un tableau.  Un tableau qui contient le total des ventes pour chaque jour du mois possède une dimension \(le jour du mois\).  Un tableau qui contient le total des ventes par service pour chaque jour du mois possède deux dimensions \(le numéro du service et le jour du mois\).  Le nombre de dimensions que possède un tableau s'appelle un *rang*.  
  
> [!NOTE]
>  Vous pouvez utiliser la propriété <xref:System.Array.Rank%2A> pour déterminer le nombre de dimensions d'un tableau.  
  
## Utilisation des dimensions  
 Spécifiez un élément d'un tableau en fournissant un *index* ou un *indice* pour chacune de ses dimensions.  Les éléments sont contigus pour chaque dimension, de l'index 0 à l'index le plus élevé de cette dimension.  
  
 Les illustrations suivantes montrent la structure conceptuelle de tableaux possédant des rangs différents.  Chaque élément dans les illustrations affiche les valeurs d'index qui y accèdent.  Par exemple, vous pouvez accéder au premier élément de la deuxième ligne du tableau à deux dimensions en spécifiant les index `(1, 0)`.  
  
 ![Diagramme graphique d'un tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.png "ArrayExDimOne")  
Tableau unidimensionnel  
  
 ![Diagramme graphique d'un tableau bidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
Tableau à deux dimensions  
  
 ![Diagramme graphique d'un tableau tridimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.png "ArrayExDimThree")  
Tableau à trois dimensions  
  
### Unidimensionnel  
 De nombreux tableaux ont une seule dimension, telle que le nombre de personnes pour chaque âge.  La seule condition pour spécifier un élément est l'âge pour lequel cet élément possède le compte.  Par conséquent, ce type de tableau utilise un seul index.  L'exemple suivant déclare une variable destinée à contenir un *tableau unidimensionnel* de comptes de personnes âgées de 0 à 120 ans.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### Deux dimensions  
 Certains tableaux ont deux dimensions, telles que le nombre de bureaux à chaque étage dans chaque bâtiment d'un campus.  La spécification d'un élément requiert à la fois le numéro du bâtiment et de l'étage, et chaque élément possède le compte pour cette combinaison de bâtiment et d'étage.  Par conséquent, ce type de tableau utilise deux index.  L'exemple suivant déclare une variable destinée à contenir un *tableau à deux dimensions* de comptes de bureau, pour des bâtiments allant de 0 à 40 et les étages de 0 à 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Un tableau à deux dimensions est également appelé *tableau rectangulaire*.  
  
### Trois dimensions  
 Certains tableaux ont trois dimensions, telles que des valeurs dans un espace tridimensionnel.  Ce type de tableau utilise trois index qui, dans le cas présent, correspondent aux coordonnées x, y et z de l'espace physique.  L'exemple suivant déclare une variable destinée à contenir un *tableau à trois dimensions* de températures de l'air à plusieurs endroits dans un volume tridimensionnel.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### Plus de trois dimensions  
 Bien qu'un tableau puisse avoir jusqu'à 32 dimensions, il est rare d'en avoir plus de trois.  
  
> [!NOTE]
>  Lorsque vous ajoutez des dimensions à un tableau, le stockage total nécessaire pour le tableau augmente considérablement. Utilisez donc les tableaux multidimensionnels avec prudence.  
  
## Utilisation de dimensions différentes  
 Supposons que vous souhaitez effectuer le suivi des montants des ventes pour chaque jour du mois en cours.  Vous pouvez déclarer un tableau unidimensionnel avec 31 éléments, un pour chaque jour du mois, comme le montre l'exemple suivant.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Supposons maintenant que vous souhaitez effectuer le suivi des mêmes informations non seulement pour chaque jour du mois, mais également pour chaque mois de l'année.  Vous pouvez déclarer un tableau à deux dimensions avec 12 lignes \(pour les mois\) et 31 colonnes \(pour les jours\), comme le montre l'exemple suivant.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Maintenant supposons que vous décidez que votre tableau stockera des informations pendant plus d'une année.  Si vous souhaitez effectuer le suivi des montants des ventes sur 5 ans, vous pouvez déclarer un tableau à trois dimensions composé de 5 couches, de 12 lignes et de 31 colonnes, comme le montre l'exemple suivant.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Étant donné que chaque index varie de 0 à son maximum, notez que chaque dimension de `salesAmounts` est déclarée avec une valeur inférieure de 1 à la longueur requise pour cette dimension.  Notez également que la taille du tableau augmente avec chaque nouvelle dimension.  Les trois tailles dans les exemples précédents sont respectivement 31, 372 et 1 860 éléments.  
  
> [!NOTE]
>  Vous pouvez créer un tableau sans utiliser l'instruction `Dim` ou la clause `New`.  Par exemple, vous pouvez appeler la méthode <xref:System.Array.CreateInstance%2A>, ou un autre composant peut passer à votre code un tableau créé de cette manière.  Ce type de tableau peut avoir une limite inférieure différente de 0.  Vous pouvez toujours tester la limite inférieure d'une dimension à l'aide de la méthode <xref:System.Array.GetLowerBound%2A> ou de la fonction `LBound`.  
  
## Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)