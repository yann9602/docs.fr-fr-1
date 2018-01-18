---
title: FUNCTION (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 957c31d3262e5c97d576d444748bd1979aee0ce0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="function-entity-sql"></a>FUNCTION (Entity SQL)
Définit une fonction dans la portée d'une commande de requête Entity SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Arguments  
 `function-name`  
 Nom de la fonction.  
  
 `parameter-name`  
 Nom d'un paramètre dans la fonction.  
  
 `function_expression`  
 Expression Entity SQL valide qui correspond à la fonction. La commande dans la fonction peut agir sur les paramètres `parameter_name` transmis à la fonction.  
  
 `data_type`  
 Nom d'un type pris en charge.  
  
 COLLECTION ( <type_definition`>` )  
 Expression qui retourne une collection de types, lignes ou références pris en charge.  
  
 REF **(**`data_type`**)**  
 Expression qui retourne une référence à un type d'entité.  
  
 ROW **(**`row_expression`**)**  
 Expression qui retourne des enregistrements anonymes, structurellement typés à partir d'une ou plusieurs valeurs. Pour plus d'informations, consultez [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Notes  
 Plusieurs fonctions du même nom peuvent être déclarées inline, à condition que les signatures des fonctions soient différentes. Pour plus d'informations, consultez [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Une fonction incluse peut être appelée dans une commande Entity SQL après seulement qu'elle a été définie dans cette commande. Toutefois, une fonction incluse peut être appelée au sein d'une autre fonction incluse avant ou après la définition de la fonction appelée. Dans l'exemple suivant, la fonction  A appelle la fonction B avant que la fonction  B soit définie :  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Pour plus d’informations, consultez [Comment : appeler une fonction définie par l’utilisateur](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 Les fonctions peuvent également être déclarées dans le modèle lui-même. Les fonctions déclarées dans le modèle sont exécutées de la même façon que les fonctions déclarées inline dans la commande. Pour plus d’informations, consultez [les fonctions définies par l’utilisateur](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Exemple  
 La commande Entity SQL suivante définit une fonction `Products` qui accepte une valeur entière pour filtrer les produits retournés.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Exemple  
 La commande Entity SQL suivante définit une fonction `StringReturnsCollection` qui accepte une collection de chaînes pour filtrer les contacts retournés.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Langage Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
