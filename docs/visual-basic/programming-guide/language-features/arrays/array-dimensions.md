---
title: Dimensions du tableau dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a>Dimensions du tableau dans Visual Basic
A *dimension* est une direction dans laquelle vous pouvez varier la spécification des éléments d’un tableau. Un tableau qui contient les ventes totales pour chaque jour du mois possède une dimension (le jour du mois). Un tableau qui contient les ventes totales par service pour chaque jour du mois possède deux dimensions (le numéro de service et le jour du mois). Le nombre de dimensions dispose d’un tableau est appelé son *rang*.  
  
> [!NOTE]
>  Vous pouvez utiliser le <xref:System.Array.Rank%2A> propriété pour déterminer le nombre de dimensions d’un tableau.  
  
## <a name="working-with-dimensions"></a>Utilisation des Dimensions  
 Vous spécifiez un élément d’un tableau en fournissant un *index* ou *indice* pour chacune de ses dimensions. Les éléments sont contigus pour chaque dimension de l’index 0 dans l’index le plus élevé pour cette dimension.  
  
 Les illustrations suivantes montrent la structure conceptuelle de tableaux avec des classements différents. Chaque élément dans les illustrations affiche les valeurs d’index qui y accéder. Par exemple, vous pouvez accéder le premier élément de la deuxième ligne du tableau à deux dimensions en spécifiant les index `(1, 0)`.  
  
 ![Diagramme graphique d’un &#45; tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
Tableau unidimensionnel  
  
 ![Diagramme graphique de deux &#45; tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
Tableau à deux dimensions  
  
 ![Diagramme graphique de trois &#45; tableau unidimensionnel](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
Tableau à trois dimensions  
  
### <a name="one-dimension"></a>Une Dimension  
 De nombreux groupes ont une seule dimension, telles que le nombre de personnes pour chaque âge. La seule exigence pour spécifier un élément est la durée de vie pour laquelle cet élément conserve le nombre. Par conséquent, ce type de tableau utilise un seul index. L’exemple suivant déclare une variable qui doit contenir un *tableau unidimensionnel* d’âge du nombre d’âgés de 0 à 120.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>Deux Dimensions  
 Certains tableaux ont deux dimensions, telles que le nombre de bureaux à chaque étage de chaque génération sur un site. La spécification d’un élément requiert à la fois le numéro du bâtiment et l’étage, et chaque élément possède le compte pour cette combinaison de bâtiment et étage. Par conséquent, ce type de tableau utilise deux index. L’exemple suivant déclare une variable qui doit contenir un *tableau à deux dimensions* de comptes de bureau, pour les bâtiments 0 à 40 et planchers 0 à 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 Un tableau à deux dimensions est également appelé un *tableau rectangulaire*.  
  
### <a name="three-dimensions"></a>Trois Dimensions  
 Certains tableaux ont trois dimensions, telles que les valeurs dans l’espace à trois dimensions. Ce type de tableau utilise trois index, qui dans ce cas représentent le x, y et les coordonnées z de l’espace physique. L’exemple suivant déclare une variable qui doit contenir un *tableau tridimensionnel* de température à différents points dans un volume en trois dimensions.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Plus de trois Dimensions  
 Un tableau peut avoir jusqu'à 32 dimensions, mais il est rare d’avoir plus de trois.  
  
> [!NOTE]
>  Lorsque vous ajoutez des dimensions à un tableau, le stockage total nécessaire pour le tableau augmente considérablement, c’est le cas des tableaux multidimensionnels utiliser avec précaution.  
  
## <a name="using-different-dimensions"></a>À l’aide de différentes Dimensions  
 Supposons que vous souhaitez effectuer le suivi des montants des ventes pour tous les jours du mois en cours. Vous pouvez déclarer un tableau unidimensionnel avec 31 éléments, un pour chaque jour du mois, comme l’exemple suivant montre.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Maintenant Supposons que vous souhaitez suivre les mêmes informations non seulement pour tous les jours du mois, mais également pour chaque mois de l’année. Vous pouvez déclarer un tableau à deux dimensions avec 12 lignes (pour les mois) et 31 colonnes (pour les jours), comme le montre l’exemple suivant.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Supposons que vous voulez que votre tableau contiennent à présent des informations pour plusieurs années. Si vous souhaitez effectuer le suivi des montants des ventes pendant 5 ans, vous pouviez déclarer un tableau tridimensionnel avec 5 couches, de 12 lignes et de 31 colonnes, comme le montre l’exemple suivant.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Notez que, étant donné que chaque index varie de 0 à sa valeur maximale, chaque dimension du `salesAmounts` est déclaré comme un de moins que la longueur requise pour cette dimension. Notez également que la taille du tableau augmente avec chaque nouvelle dimension. Les trois tailles dans les exemples précédents sont respectivement 31, 372 et 1 860 éléments.  
  
> [!NOTE]
>  Vous pouvez créer un tableau sans utiliser le `Dim` instruction ou `New` clause. Par exemple, vous pouvez appeler la <xref:System.Array.CreateInstance%2A> méthode ou un autre composant peut passer à votre code un tableau créé de cette manière. Ce type de tableau peut avoir une limite inférieure différente de 0. Vous pouvez toujours tester la limite inférieure d’une dimension à l’aide de la <xref:System.Array.GetLowerBound%2A> méthode ou la `LBound` (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dépannage des tableaux](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
