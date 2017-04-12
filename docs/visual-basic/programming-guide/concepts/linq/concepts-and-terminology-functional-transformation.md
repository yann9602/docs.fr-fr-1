---
title: Concepts et terminologie (Transformation fonctionnelle) (Visual Basic) | Documents Microsoft
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
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c4716765199798e50c4318b290f8a2d76ef5841
ms.lasthandoff: 03/13/2017


---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Concepts et terminologie (Transformation fonctionnelle) (Visual Basic)
Cette rubrique présente les concepts et la terminologie des transformations fonctionnelles pures. L'approche de transformation fonctionnelle pour la transformation des données génère du code qui est souvent plus rapide à programmer, plus expressif et plus facile à déboguer et à maintenir que le code de programmation impératif plus traditionnel.  
  
 Notez que les rubriques de cette section n'ont pas pour but d'expliquer en détail la programmation fonctionnelle. Au lieu de cela, elles identifient certaines des capacités de programmation fonctionnelle qui facilitent la transformation de code XML d'une forme en une autre.  
  
## <a name="what-is-pure-functional-transformation"></a>Qu'est-ce que la transformation fonctionnelle pure ?  
 Dans *transformation fonctionnelle pure*, un ensemble de fonctions, appelées *les fonctions pures*, définissent comment transformer un ensemble de données structurées à partir de sa forme d’origine en une autre forme. Le terme « pur » indique que les fonctions sont *composable*, ce qui nécessite qu’elles soient :  
  
-   *Autonome*, afin qu’ils peuvent être librement ordonnées et réorganisées sans enchevêtrement ni interdépendance avec le reste du programme. Les transformations pures n'ont aucune connaissance de leur environnement et aucun effet sur lui. Autrement dit, les fonctions utilisées dans la transformation n’ont pas *effets*.  
  
-   *Sans état*, afin que l’exécution de la même fonction ou un ensemble de fonctions sur la même entrée génèrera toujours dans la même sortie. Les transformations pures n'ont pas de mémoire de leur utilisation antérieure.  
  
> [!IMPORTANT]
>  Dans le reste de ce didacticiel, le terme « fonction pure » est utilisé dans un sens général pour indiquer une approche de programmation, et non une fonctionnalité de langage spécifique.  
>   
>  Notez que les fonctions pures doivent être implémentées en tant que fonctions en Visual Basic.  
>   
>  En outre, il convient de ne pas confondre les fonctions pures avec les méthodes virtuelles pures en C++. Ces dernières indiquent que la classe conteneur est abstraite et qu'aucun corps de méthode n'est fourni.  
  
### <a name="functional-programming"></a>Programmation fonctionnelle  
 *Programmation fonctionnelle* est une approche de programmation qui prend en charge directement la transformation fonctionnelle pure.  
  
 Historiquement, des langages de programmation fonctionnelle à usage général, tels que ML, schéma, Haskell et F #, ont été principalement de l’intérêt pour la Communauté universitaire. Bien qu’il a toujours été possible d’écrire des transformations fonctionnelles pures en Visual Basic, la difficulté de cette opération donc pas rend une option intéressante pour la plupart des programmeurs. Avec les versions ultérieures de Visual Basic, toutefois, nouvelles constructions de langage telles que les expressions lambda et l’inférence de type rendent la programmation fonctionnelle beaucoup plus facile et plus productive.  
  
 Pour plus d’informations sur la programmation fonctionnelle, consultez [vs programmation fonctionnelle. La programmation impérative (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Langages de programmation fonctionnelle spécifiques aux domaines  
 Bien que les langages de programmation fonctionnelle généraux n'aient pas été adoptés à grande échelle, les langages de programmation fonctionnelle spécifiques aux domaines ont eu un meilleur succès. Par exemple, les feuilles de style en cascade (CSS, Cascading Style Sheets) sont utilisées pour déterminer l’apparence et la convivialité de nombreuses pages web et les feuilles de style XSLT (Extensible Stylesheet Language Transformations) sont utilisées de manière intensive dans la manipulation de données XML. Pour plus d’informations sur XSLT, voir [Transformations XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03).  
  
## <a name="terminology"></a>Terminologie  
 Le tableau suivant définit certains termes liés aux transformations fonctionnelles.  
  
 fonction d'ordre supérieur (première classe)  
 Fonction qui peut être traitée en tant qu'objet de programmation. Par exemple, une fonction d'ordre supérieur peut être passée à ou retournée à partir d'autres fonctions. Dans Visual Basic, les délégués et les expressions lambda sont des fonctionnalités qui prennent en charge les fonctions d’ordre supérieur. Pour écrire une fonction d’ordre supérieur, vous déclarez un ou plusieurs arguments pour prendre des délégués et vous utilisez souvent des expressions lambda lorsque vous appelez votre fonction. Une grande partie des opérateurs de requête standard sont des fonctions d'ordre supérieur.  
  
 Pour plus d’informations, consultez [vue d’ensemble Standard des opérateurs de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 expression lambda  
 Pour l'essentiel, il s'agit d'une fonction anonyme inline qui peut être utilisée partout où un type délégué est attendu. Cette définition des expressions lambda est simplifiée, mais elle convient pour les besoins de ce didacticiel.  
  
 Pour plus d’informations, consultez [Expressions Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 collection  
 Ensemble structuré de données, généralement d'un type uniforme. Pour être compatible avec LINQ, une collection doit implémenter le <xref:System.Collections.IEnumerable>interface ou <xref:System.Linq.IQueryable>interface (ou l’un de leurs équivalents génériques, <xref:System.Collections.Generic.IEnumerator%601>ou <xref:System.Linq.IQueryable%601>).</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerator%601> </xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable>  
  
 tuple (types anonymes)  
 Concept mathématique, un tuple est une séquence limitée d'objets, chacun d'un type spécifique. Un tuple porte également le nom de liste ordonnée. Les types anonymes sont une implémentation linguistique de ce concept, qui permet à un type de classe non nommé d'être déclaré et à un objet de ce type d'être instancié en même temps.  
  
 Pour plus d’informations, consultez [les Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 inférence de type (typage implicite)  
 Capacité d'un compilateur à déterminer le type d'une variable en l'absence d'une déclaration de type explicite.  
  
 Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 exécution différée et évaluation différée  
 Action de retarder l'évaluation d'une expression jusqu'à ce que sa valeur résolue soit réellement nécessaire. L’exécution différée est prise en charge dans les collections.  
  
 Pour plus d’informations, consultez [base des opérations de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) et [exécution différée et évaluation différées dans LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Ces fonctionnalités de langage seront utilisés dans les exemples de code tout au long de cette section.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux Transformations fonctionnelles pures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [Comparaison de la programmation fonctionnelle et de la Programmation impérative (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
