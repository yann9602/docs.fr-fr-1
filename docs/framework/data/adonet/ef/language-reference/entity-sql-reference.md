---
title: "Référence Entity SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 776a2a93f559ba54651adc49e6b609c8156e9e31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-sql-reference"></a>Référence Entity SQL
Cette section contient des rubriques de référence sur [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Cette rubrique résume et regroupe les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs par catégorie.  
  
## <a name="arithmetic-operators"></a>Opérateurs arithmétiques  
 Les opérateurs arithmétiques effectuent des opérations mathématiques sur deux expressions d'au moins un type numérique. Le tableau ci-dessous répertorie les opérateurs arithmétiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Utilisation|  
|--------------|---------|  
|[+ (Addition)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|Addition|  
|« / (Division) »|Division|  
|[% (Modulo)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|Retourne le reste d'une division.|  
|[* (Multiplication)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|Multiplication|  
|[-(Négatif)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|Négation.|  
|[-(Soustraction)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|Soustraction|  
  
## <a name="canonical-functions"></a>Fonctions canoniques  
 Les fonctions canoniques sont prises en charge par tous les fournisseurs de données et peuvent être utilisées par toutes les technologies de requête. Le tableau ci-dessous répertorie les fonctions canoniques.  
  
|Fonction|Type|  
|--------------|----------|  
|[Fonctions canoniques d’agrégation Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|Décrit les fonctions canoniques d'agrégation [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions canoniques mathématiques](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|Décrit les fonctions canoniques mathématiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions canoniques de chaîne](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|Décrit les fonctions canoniques de chaîne [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Fonctions canoniques de date et d’heure](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Décrit les fonctions canoniques de date et d'heure [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Au niveau du bit des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Décrit les fonctions canoniques au niveau du bit [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[Les autres fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|Décrit les fonctions qui ne sont pas considérées comme des fonctions au niveau du bit, des fonctions de date/heure, des fonctions de chaîne, des fonctions mathématiques ni des fonctions d'agrégation.|  
  
## <a name="comparison-operators"></a>Opérateurs de comparaison  
 Des opérateurs de comparaison sont définis pour les types suivants : `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time`, `DateTimeOffset`. La promotion de type implicite intervient pour les opérandes avant application de l'opérateur de comparaison. Les opérateurs de comparaison produisent toujours des valeurs booléennes. Lorsque au moins l'un des opérandes est `null`, le résultat est `null`.  
  
 L'égalité et l'inégalité sont définies pour tout type d'objet qui possède une identité, comme le type `Boolean`. Les objets non primitifs possédant une identité sont considérés comme égaux s'ils partagent la même identité. Le tableau ci-dessous répertorie les opérateurs de comparaison [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[= (Égal)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|Compare l'égalité de deux expressions.|  
|[> (Supérieur à)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure à celle de l'expression de droite.|  
|[> = (supérieur ou égal à)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite.|  
|[EST &#91; PAS &#93; VALEUR NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|Détermine si une expression de requête a la valeur NULL.|  
|[< (Inférieur à)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure à celle de l'expression de droite.|  
|[< = (inférieur ou égal à)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si la valeur de l'expression de gauche est inférieure ou égale à celle de l'expression de droite.|  
|[&#91; PAS &#93; ENTRE](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|Détermine si une expression a pour résultat une valeur contenue dans une plage spécifiée.|  
|[! = (Différent de)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite.|  
|[&#91; PAS &#93; COMME](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|Détermine si une chaîne de caractères donnée correspond à un modèle spécifié.|  
  
## <a name="logical-and-case-expression-operators"></a>Opérateurs logiques et opérateurs d'expression CASE  
 Les opérateurs logiques testent le caractère vrai ou faux d'une condition. L'expression CASE évalue un ensemble d'expressions booléennes pour déterminer le résultat. Le tableau ci-dessous répertorie les opérateurs logiques et d'expression CASE.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[& & (AND logique)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|AND logique|  
|[!, (NOT logique)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|NOT logique.|  
|[&#124; &#124; (Ou logique)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|OR logique|  
|[CAS](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|Évalue un ensemble d'expressions booléennes pour déterminer le résultat.|  
|[PUIS](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|Le résultat d’une [lorsque](http://msdn.microsoft.com/en-us/6233fe9f-00b0-460e-8372-64e138a5f998) clause lorsqu’il a la valeur true.|  
  
## <a name="query-operators"></a>Opérateurs de requête  
 Les opérateurs de requête permettent de définir des expressions de requête qui retournent des données d'entité. Le tableau ci-dessous répertorie les opérateurs de requête.  
  
|Opérateur|Utilisation|  
|--------------|---------|  
|[DE](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|Spécifie la collection qui est utilisée dans [sélectionnez](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instructions.|  
|[REGROUPER PAR](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|Spécifie les groupes dans les objets qui sont retournés par une requête ([sélectionnez](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression doivent être placés.|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|Retourne une collection de valeurs d’argument, projetées en dehors de la partition de groupe à laquelle l’agrégat est associé.|  
|[AVOIR](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|Spécifie une condition de recherche pour un groupe ou un agrégat.|  
|[LIMITE](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|Utilisé avec le [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause pour effectuer une pagination physique.|  
|[TRIER PAR](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|Spécifie l’ordre de tri utilisé sur les objets retournés dans un [sélectionnez](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instruction.|  
|[SÉLECTIONNEZ](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|Spécifie les éléments dans la projection qui sont retournés par une requête.|  
|[IGNORER](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|Utilisé avec le [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause pour effectuer une pagination physique.|  
|[RETOUR AU DÉBUT](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|Spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.|  
|[OÙ](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|Filtre de manière conditionnelle les données qui sont retournées par une requête.|  
  
## <a name="reference-operators"></a>Opérateurs de référence  
 Une référence est un pointeur logique (clé étrangère) vers une entité spécifique dans un jeu d'entités spécifique. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prend en charge les opérateurs suivants pour construire, déconstruire et Explorer les références.  
  
|Opérateur|Utilisation|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|Crée les références à une entité dans un jeu d'entités.|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|Déréférence une valeur de référence et génère le résultat de ce déréférencement.|  
|[CLÉ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|Extrait la clé d'une référence ou d'une expression d'entité.|  
|[ACCÉDEZ](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|Vous permet de naviguer sur la relation d'un type d'entité jusqu'à un autre|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|Retourne une référence à une instance d'entité.|  
  
## <a name="set-operators"></a>Opérateurs de jeu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit diverses opérations Set performantes. Cela inclut les opérateurs de jeu aux opérateurs Transact-SQL telles que l’UNION, INTERSECT, EXCEPT et EXISTS. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend également en charge des opérateurs pour l'élimination des doublons (SET), les tests d'appartenance (IN) et les jointures (JOIN). Le tableau ci-dessous répertorie les opérateurs Set [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Opérateur|Utilisation|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|Extrait un élément d'une collection à valeurs multiples.|  
|[À L’EXCEPTION](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|Retourne une collection de valeurs distinctes à partir de l'expression de requête située du côté gauche de l'opérande EXCEPT, qui ne sont pas retournées à partir de l'expression de requête située à droite de l'opérande EXCEPT.|  
|[&#91; PAS &#93; IL EXISTE](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|Détermine si une collection est vide.|  
|[APLATIR](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|Convertit une collection de collections en collection plane.|  
|[&#91; PAS &#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|Détermine si une valeur correspond à une valeur incluse dans une collection.|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|Retourne une collection de valeurs distinctes qui sont retournées par les expressions de requête tant à gauche qu'à droite de l'opérande INTERSECT.|  
|[CHEVAUCHEMENTS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|Détermine si deux collections ont des éléments en commun.|  
|[ENSEMBLE](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|Permet de convertir une collection d’objets en un ensemble en produisant une nouvelle collection dans laquelle tous les éléments en double ont été supprimés.|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|Combine les résultats de deux requêtes, ou plus, en une collection unique.|  
  
## <a name="type-operators"></a>Opérateurs de type  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]fournit les opérations qui permettent le type d’une expression (valeur) à être construit, l’interrogation et manipulé. Le tableau ci-dessous répertorie les opérateurs qui permettent d'utiliser les types.  
  
|Opérateur|Utilisation|  
|--------------|---------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|Convertit une expression d'un type de données à un autre.|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|Utilisé dans un [fonction](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) opération pour déclarer une collection de types d’entité ou des types complexes.|  
|[EST &#91; PAS &#93; DE](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous-types.|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|Retourne une collection d'objets à partir d'une expression de requête d'un type spécifique.|  
|[Constructeur de Type nommé](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|Permet de créer des instances de types d'entités ou de types complexes.|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|Crée une instance d'un multiensemble à partir d'une liste de valeurs.|  
|[LIGNE](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|Construit des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|Traite un objet d'un type de base déterminé en tant qu'objet du type dérivé spécifié.|  
  
## <a name="other-operators"></a>Autres opérateurs  
 Le tableau suivant répertorie les autres [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs.  
  
|Opérateur|Utilisation|  
|--------------|---------|  
|[+ (Concaténation de chaîne)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|Permet de concaténer des chaînes dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[. (accès aux membres)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|Permet d'accéder à la valeur d'une propriété ou d'un champ d'une instance de type de modèle conceptuel structurel.|  
|[--(Commentaire)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|Inclure des commentaires [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[(FONCTION)](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Définit une fonction incluse qui peut être exécutée dans une requête Entity SQL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Langage Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
