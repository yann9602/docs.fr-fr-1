---
title: "Fonctions de chaînes canoniques au niveau du bit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a20f9675af5a67291d95a9297b1ffa1c81a80522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-canonical-functions"></a>Fonctions de chaînes canoniques au niveau du bit
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] inclut des fonctions canoniques au niveau du bit.  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant présente les autres fonctions canoniques [!INCLUDE[esql](../../../../../../includes/esql-md.md)] au niveau du bit. Ces fonctions retournent `Null` si `Null` entrée est fournie. Le type de retour des fonctions est le même que le ou les types d’arguments. Les arguments doivent être du même type si la fonction prend plusieurs arguments. Pour effectuer des opérations au niveau du bit sur différents types, vous devez effectuer un cast explicite vers le même type.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Retourne la conjonction au niveau du bit de `value1` et de `value2` comme type de `value1` et de `value2`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32`, et `Int64`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Retourne la négation au niveau du bit de `value`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32`, et `Int64`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Retourne la disjonction au niveau du bit de `value1` et de `value2` comme type de `value1` et de `value2`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32` et `Int64`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Retourne la disjonction exclusive au niveau du bit de `value1` et de `value2` comme type de `value1` et de `value2`.<br /><br /> **Arguments**<br /><br /> A `Byte`, `Int16`, `Int32` et `Int64`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
