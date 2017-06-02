---
title: "LIKE (Entity SQL) | Microsoft Docs"
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
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LIKE (Entity SQL)
Détermine si une `String` de caractères donnée correspond à un modèle spécifié.  
  
## Syntaxe  
  
```  
  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## Arguments  
 `match`  
 Expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui prend la valeur `String`.  
  
 `pattern`  
 Modèle devant correspondre à la valeur `String` spécifiée.  
  
 `escape`  
 Caractère d'échappement.  
  
 NOT  
 Indique que la valeur du résultat de l'opérateur LIKE est inversée.  
  
## Valeur de retour  
 `true` si la `string` correspond au modèle ; sinon, `false`.  
  
## Notes  
 Les expressions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui utilisent l'opérateur LIKE sont évaluées de façon très similaire aux expressions qui utilisent l'égalité comme critère de filtre. Toutefois, les expressions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui utilisent l'opérateur LIKE peuvent inclure des littéraux et des caractères génériques.  
  
 Le tableau ci\-dessous décrit la syntaxe de la chaîne \(`string`\) de modèle.  
  
|Caractère générique|Description|Exemple|  
|-------------------------|-----------------|-------------|  
|%|Toute chaîne \(`string`\) de zéro, un ou plusieurs caractères.|`title like '%computer%'` recherche tous les titres comprenant le mot `"computer"` .|  
|\_ \(caractère de soulignement\)|N'importe quel caractère unique.|`firstname like '_ean'` recherche tous les prénoms de quatre lettres qui se terminent par  `"ean`" comme Jean ou Sean.|  
|\[ \]|Tout caractère unique se trouvant dans la plage \(\[a\-f\]\) ou l'ensemble spécifié \(\[abcdef\]\).|`lastname like '[C-P]arsen'` recherche les noms de famille se terminant par « arsen » et commençant par n'importe quel caractère unique compris entre C et P, tels que Carsen ou Larsen.|  
|\[^\]|Tout caractère unique ne se trouvant pas dans la plage \(\[^a\-f\]\) ou l'ensemble spécifié \(\[^abcdef\]\).|`lastname like 'de[^l]%'` recherche tous les noms de famille qui commencent par « de » et dont la lettre suivante n'est pas un « l ».|  
  
> [!NOTE]
>  L'opérateur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE et la clause ESCAPE ne peuvent pas être appliqués aux valeurs de `System.DateTime` ou `System.Guid`.  
  
 L'opérateur LIKE prend en charge les critères spéciaux ASCII et Unicode. Lorsque tous les paramètres sont des caractères ASCII, une recherche générique ASCII est effectuée. Si un ou plusieurs arguments sont de type Unicode, tous les arguments sont convertis en Unicode et une recherche générique Unicode est effectuée. Lors de l'utilisation de données Unicode avec LIKE, les espaces de droite sont significatifs ; pour les autres données, cependant, ils ne le sont pas. La syntaxe des chaînes de modèle d'[!INCLUDE[esql](../../../../../../includes/esql-md.md)] est identique à celle de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Un modèle peut comporter des caractères ordinaires et des caractères génériques. Au cours de l'analyse, les caractères normaux doivent correspondre exactement aux caractères spécifiés dans la `string` de caractères. Toutefois, les caractères génériques peuvent être associés à des portions aléatoires de la chaîne de caractères. Lorsqu'il est utilisé avec des caractères génériques, l'opérateur LIKE est plus souple que les opérateurs de comparaison de chaînes « \= » et « \!\= ».  
  
> [!NOTE]
>  Vous pouvez utiliser des extensions spécifiques au fournisseur si vous ciblez un fournisseur spécifique. Toutefois, de telles constructions peuvent être traitées différemment par d'autres fournisseurs, par exemple. SqlServer prend en charge les modèles \[first\-last\] et \[^first\-last\]. Le premier modèle correspond exactement à un caractère compris entre les premier et dernier caractères, tandis que le second modèle correspond exactement à un caractère non compris entre les premier et dernier caractères.  
  
### Échap  
 En utilisant la clause ESCAPE, vous pouvez rechercher des chaînes de caractères qui contiennent un ou plusieurs des caractères génériques spéciaux décrits dans le tableau de la section précédente. Par exemple, supposons que plusieurs documents contiennent le littéral « 100 % » dans le titre et que vous souhaitez rechercher tous ces documents. Le caractère de pourcentage \(%\) étant un caractère générique, vous devez le placer dans une séquence d'échappement par le biais de la clause [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE pour exécuter la recherche avec succès. Voici un exemple de ce filtre :  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 Dans cette expression de recherche, le caractère générique de pourcentage \(%\) qui suit immédiatement le point d'exclamation \(\!\) est traité comme un littéral et non comme un caractère générique. Vous pouvez utiliser n'importe quel caractère en guise de caractère d'échappement à l'exception des caractères génériques [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et des crochets \(`[ ]`\). Dans l'exemple précédent, le point d'exclamation \(\!\) fait office de caractère d'échappement.  
  
## Exemple  
 Les deux requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci\-dessous utilisent les opérateurs LIKE et ESCAPE pour déterminer si une chaîne de caractères spécifique correspond à un modèle spécifié. La première requête recherche le `Name` qui commence par les caractères `Down_`. Cette requête utilise l'option ESCAPE car le caractère de soulignement \(`_`\) est un caractère générique. Sans l’option ESCAPE, la requête rechercherait toutes les valeurs `Name` commençant par le mot `Down` suivi de tout caractère unique autre que le caractère de soulignement. Les requêtes sont basées sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure indiquée dans [Procédure : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)