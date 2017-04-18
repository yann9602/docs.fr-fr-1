---
title: "LINQ et chaînes (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a79d1427331070da9c545fdd3175115fe187e879
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-strings-visual-basic"></a>LINQ et chaînes (Visual Basic)
LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Il peut être particulièrement utile avec les données semi-structurées dans les fichiers texte. Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières. Par exemple, vous pouvez utiliser la <xref:System.String.Split%2A>ou <xref:System.Text.RegularExpressions.Regex.Split%2A>pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier en utilisant LINQ.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A> Vous pouvez utiliser la <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>méthode dans le `where` clause d’une requête LINQ.</xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Et vous pouvez utiliser LINQ pour interroger ou modifier le <xref:System.Text.RegularExpressions.MatchCollection>les résultats retournés par une expression régulière.</xref:System.Text.RegularExpressions.MatchCollection>  
  
 Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données de texte semi-structurées en XML. Pour plus d’informations, consultez [Comment : générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md).  
  
 Les exemples de cette section se répartissent en deux catégories :  
  
## <a name="querying-a-block-of-text"></a>Interrogation d’un bloc de texte  
 Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en un tableau requêtable de plus petites chaînes à l’aide de la <xref:System.String.Split%2A>méthode ou <xref:System.Text.RegularExpressions.Regex.Split%2A>méthode.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A> Vous pouvez fractionner le texte source en mots, phrases, paragraphes, pages ou d’autres critères et puis effectuer des fractionnements supplémentaires s’ils sont requis dans votre requête.  
  
 [Comment : compter les Occurrences d’un mot dans une chaîne (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Montre comment utiliser LINQ pour les interrogations simples sur le texte.  
  
 [Comment : rechercher des phrases qui contiennent un jeu spécifié de mots (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.  
  
 [Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Montre qu’une chaîne est un type requêtable.  
  
 [Comment : combiner des requêtes LINQ avec des Expressions régulières (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Montre comment utiliser des expressions régulières dans les requêtes LINQ pour les critères spéciaux complexes sur les résultats de requête filtrée.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Interrogation des données semi-structurées au Format texte  
 Différents types de fichiers texte sont constitués d’une série de lignes, généralement avec la même mise en forme, telles que les fichiers délimité par des tabulations ou des virgules ou des lignes de longueur fixe. Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes. Requêtes LINQ simplifient également la combinaison des données provenant de plusieurs sources.  
  
 [Comment : rechercher la différence définie entre deux listes (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Montre comment rechercher toutes les chaînes qui sont présents dans une liste, mais pas l’autre.  
  
 [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Montre comment trier les lignes de texte en fonction de n’importe quel mot ou le champ.  
  
 [Comment : réorganiser les champs d’un fichier délimité (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Montre comment réorganiser les champs dans une ligne dans un fichier .csv.  
  
 [Comment : combiner et comparer des Collections de chaînes (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Montre comment combiner des listes de chaîne de différentes manières.  
  
 [Comment : remplir des Collections d’objets issues de plusieurs Sources (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.  
  
 [Comment : joindre du contenu issu de différents fichiers (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Montre comment combiner des chaînes dans deux listes en une seule chaîne à l’aide d’une clé correspondante.  
  
 [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Montre comment créer des fichiers à l’aide d’un seul fichier comme source de données.  
  
 [Comment : calculer des valeurs de colonne dans un fichier de texte CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.  
  
## <a name="see-also"></a>Voir aussi  
 [Language-Integrated Query (LINQ) (Visual Basic)](index.md)   
 [Guide pratique : générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md)

