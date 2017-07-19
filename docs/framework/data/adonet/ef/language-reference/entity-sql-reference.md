---
title: "R&#233;f&#233;rence Entity SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# R&#233;f&#233;rence Entity SQL
Cette section contient des rubriques de référence [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Cette rubrique récapitule et groupe les opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] par catégorie.  
  
## Opérateurs arithmétiques  
 Les opérateurs arithmétiques effectuent des opérations mathématiques sur deux expressions d'au moins un type numérique.  Le tableau ci\-dessous répertorie les opérateurs arithmétiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Utilisez|  
|---------------|--------------|  
|[\+ \(Ajouter\)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|Addition|  
|[\/ \(Divide\)](../../../../../../docs/framework/data/adonet/ef/language-reference/divide-entity-sql.md)|Division|  
|[% \(Modulo\)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|Retourne le reste d'une division.|  
|[\* \(Multiplier\)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|Multiplication|  
|[\- \(négatif\)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|Négation.|  
|[\- \(soustraction\)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|Soustraction|  
  
## Fonctions canoniques  
 Les fonctions canoniques sont prises en charge par tous les fournisseurs de données et peuvent être utilisées par toutes les technologies de requête.  Le tableau ci\-dessous répertorie les fonctions canoniques.  
  
|Fonction|Type|  
|--------------|----------|  
|[Fonctions canoniques Entity SQL d'agrégation](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|Décrit les fonctions canoniques d'agrégation [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions mathématiques canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|Décrit les fonctions canoniques mathématiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions de chaînes canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|Décrit les fonctions canoniques de chaîne [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions de date et d'heure canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Décrit les fonctions canoniques de date et d'heure [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions de chaînes canoniques au niveau du bit](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Décrit les fonctions canoniques au niveau du bit [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Autres fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|Décrit les fonctions qui ne sont pas considérées comme des fonctions au niveau du bit, des fonctions de date\/heure, des fonctions de chaîne, des fonctions mathématiques ni des fonctions d'agrégation.|  
  
## Opérateurs de comparaison  
 Des opérateurs de comparaison sont définis pour les types suivants : `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time`, `DateTimeOffset`.  La promotion de type implicite intervient pour les opérandes avant application de l'opérateur de comparaison.  Les opérateurs de comparaison produisent toujours des valeurs booléennes.  Lorsque au moins l'un des opérandes est `null`, le résultat est `null`.  
  
 L'égalité et l'inégalité sont définies pour tout type d'objet qui possède une identité, comme le type `Boolean`.  Les objets non primitifs possédant une identité sont considérés comme égaux s'ils partagent la même identité.  Le tableau ci\-dessous répertorie les opérateurs de comparaison [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Description|  
|---------------|-----------------|  
|[\= \(égal à\)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|Compare l'égalité de deux expressions.|  
|[\> \(supérieur à\)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure à celle de l'expression de droite.|  
|[\>\= \(supérieur ou égal à\)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite.|  
|[IS &#91;NOT&#93; NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|Détermine si une expression de requête a la valeur NULL.|  
|[\< \(inférieur à\)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure à celle de l'expression de droite.|  
|[\<\= \(inférieur ou égal à\)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.|  
|[&#91;NOT&#93; BETWEEN](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|Détermine si une expression a pour résultat une valeur contenue dans une plage spécifiée.|  
|[\!\= \(différent de\)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite.|  
|[&#91;NOT&#93; LIKE](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|Détermine si une chaîne de caractères donnée correspond à un modèle spécifié.|  
  
## Opérateurs logiques et opérateurs d'expression CASE  
 Les opérateurs logiques testent le caractère vrai ou faux d'une condition.  L'expression CASE évalue un ensemble d'expressions booléennes pour déterminer le résultat.  Le tableau ci\-dessous répertorie les opérateurs logiques et d'expression CASE.  
  
|Opérateur|Description|  
|---------------|-----------------|  
|[&& \(AND logique\)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|AND logique|  
|[\!  \(NOT logique\)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|NOT logique.|  
|[&#124;&#124; \(OR logique\)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|OR logique|  
|[CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|Évalue un ensemble d'expressions booléennes pour déterminer le résultat.|  
|[THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|Résultat d'une clause [WHEN](http://msdn.microsoft.com/fr-fr/6233fe9f-00b0-460e-8372-64e138a5f998) lorsqu'elle a la valeur true.|  
  
## Opérateurs de requête  
 Les opérateurs de requête permettent de définir des expressions de requête qui retournent des données d'entité.  Le tableau ci\-dessous répertorie les opérateurs de requête.  
  
|Opérateur|Utilisez|  
|---------------|--------------|  
|[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|Spécifie la collection qui est utilisée dans les instructions [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md).|  
|[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|Spécifie les groupes dans lesquels doivent être placés les objets qui sont retournés par une expression de requête \([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)\).|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|Retourne une collection de valeurs d'argument, projetées en dehors de la partition de groupe à laquelle l'agrégat est associé.|  
|[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|Spécifie une condition de recherche pour un groupe ou un agrégat.|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|Utilisé avec la clause [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) pour effectuer une pagination physique.|  
|[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|Spécifie l'ordre de classement qui est utilisé sur les objets retournés dans une instruction [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md).|  
|[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|Spécifie les éléments dans la projection qui sont retournés par une requête.|  
|[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|Utilisé avec la clause [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) pour effectuer une pagination physique.|  
|[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|Spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.|  
|[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|Filtre de manière conditionnelle les données qui sont retournées par une requête.|  
  
## Opérateurs de référence  
 Une référence est un pointeur logique \(clé étrangère\) vers une entité spécifique dans un jeu d'entités spécifique.  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge les opérateurs ci\-dessous pour construire, déconstruire et explorer les références.  
  
|Opérateur|Utilisez|  
|---------------|--------------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|Crée les références à une entité dans un jeu d'entités.|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|Déréférence une valeur de référence et génère le résultat de ce déréférencement.|  
|[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|Extrait la clé d'une référence ou d'une expression d'entité.|  
|[NAVIGUER](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|Vous permet de naviguer sur la relation d'un type d'entité jusqu'à un autre|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|Retourne une référence à une instance d'entité.|  
  
## Opérateurs de jeu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit diverses opérations Set performantes.  Cela inclut les opérateurs Set qui sont similaires aux opérateurs Transact\-SQL, tels qu'UNION, INTERSECT, EXCEPT et EXISTS.  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend également en charge des opérateurs pour l'élimination des doublons \(SET\), les tests d'appartenance \(IN\) et les jointures \(JOIN\).  Le tableau ci\-dessous répertorie les opérateurs Set [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Utilisez|  
|---------------|--------------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|Extrait un élément d'une collection à valeurs multiples.|  
|[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|Retourne une collection de valeurs distinctes à partir de l'expression de requête située du côté gauche de l'opérande EXCEPT, qui ne sont pas retournées à partir de l'expression de requête située à droite de l'opérande EXCEPT.|  
|[&#91;NOT&#93; EXISTS](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|Détermine si une collection est vide.|  
|[FLATTEN](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|Convertit une collection de collections en collection plane.|  
|[&#91;NOT&#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|Détermine si une valeur correspond à une valeur incluse dans une collection.|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|Retourne une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.|  
|[OVERLAPS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|Détermine si deux collections ont des éléments en commun.|  
|[SET](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|Permet de convertir une collection d'objets en un ensemble en produisant une nouvelle collection dans laquelle tous les éléments en double ont été supprimés.|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|Combine les résultats de deux requêtes, ou plus, en une collection unique.|  
  
## Opérateurs de type  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] propose des opérations qui permettent la création, l'interrogation et la manipulation du type d'une expression \(valeur\).  Le tableau ci\-dessous répertorie les opérateurs qui permettent d'utiliser les types.  
  
|Opérateur|Utilisez|  
|---------------|--------------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|Convertit une expression d'un type de données à un autre.|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|Utilisé dans une opération [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) pour déclarer une collection de types d'entités ou de types complexes.|  
|[IS &#91;NOT&#93; OF](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous\-types.|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|Retourne une collection d'objets à partir d'une expression de requête d'un type spécifique.|  
|[Constructeur de type nommé](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|Permet de créer des instances de types d'entités ou de types complexes.|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|Crée une instance d'un multiensemble à partir d'une liste de valeurs.|  
|[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|Construit des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|Traite un objet d'un type de base déterminé en tant qu'objet du type dérivé spécifié.|  
  
## Autres opérateurs  
 Le tableau ci\-dessous répertorie les autres opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Utilisez|  
|---------------|--------------|  
|[\+ \(concaténation de chaînes\)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|Permet de concaténer des chaînes dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[.  \(accès aux membres\)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|Permet d'accéder à la valeur d'une propriété ou d'un champ d'une instance de type de modèle conceptuel structurel.|  
|[\-\- \(Commentaire\)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|Inclure des commentaires [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Définit une fonction incluse qui peut être exécutée dans une requête Entity SQL.|  
  
## Voir aussi  
 [Langage Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)