---
title: "Entity Data Model : types de données primitifs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9bf1298a5e3fbac82a931abcfb0919238d81bfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="entity-data-model-primitive-data-types"></a>Entity Data Model : types de données primitifs
Le modèle EDM (Entity Data Model) prend en charge un ensemble de types de données primitif abstrait (par exemple, String, Boolean, Int32, etc.) qui sont utilisées pour définir [propriétés](../../../../docs/framework/data/adonet/property.md) dans un modèle conceptuel. Ces types de données primitifs sont des proxys pour les types de données primitifs réels qui sont pris en charge dans l'environnement de stockage ou d'hébergement, comme une base de données SQL Server ou le Common Language Runtime (CLR). Le modèle EDM ne définit pas la sémantique des opérations ou des conversions sur les types de données primitifs ; cette sémantique est définie par l'environnement de stockage ou d'hébergement. En général, les types de données primitifs dans le modèle EDM sont mappés aux types de données primitifs correspondants dans l'environnement de stockage ou d'hébergement. Pour plus d’informations sur comment Entity Framework mappe les types primitifs dans le modèle EDM aux types de données SQL Server, consultez [SqlClient pour Entity FrameworkTypes](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  Le modèle EDM ne prend pas en charge les collections de types de données primitifs.  
  
 Pour plus d’informations sur les types de données structurées dans le modèle EDM, consultez [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) et [type complexe](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Types de données primitifs pris en charge dans le modèle EDM  
 Le tableau suivant répertorie les types de données primitifs pris en charge par le modèle EDM. Le tableau répertorie également les [facettes](../../../../docs/framework/data/adonet/facet.md) qui peut être appliqué à chaque type de données primitif.  
  
|Type de données primitif|Description|Facettes applicables|  
|-------------------------|-----------------|-----------------------|  
|Binaire|Contient des données binaires.|MaxLength, FixedLength, Nullable, Default|  
|Boolean|Contient la valeur `true` ou `false`.|Nullable, Default|  
|Byte|Contient une valeur d'entier 8 bits non signé.|Precision, Nullable, Default|  
|DateTime|Représente une date et une heure.|Precision, Nullable, Default|  
|DateTimeOffset|Contient une date et une heure en tant que décalage en minutes par rapport à l'heure GMT.|Precision, Nullable, Default|  
|Decimal|Contient une valeur numérique avec une précision et une échelle fixes.|Precision, Nullable, Default|  
|Double|Contient un nombre à virgule flottante avec une précision de 15 chiffres.|Precision, Nullable, Default|  
|Float|Contient un nombre à virgule flottante avec une précision de sept chiffres.|Precision, Nullable, Default|  
|Guid|Contient un identificateur unique de 16 octets.|Precision, Nullable, Default|  
|Int16|Contient une valeur d'entier 16 bits signé.|Precision, Nullable, Default|  
|Int32|Contient une valeur d'entier 32 bits signé.|Precision, Nullable, Default|  
|Int64|Contient une valeur d'entier 64 bits signé.|Precision, Nullable, Default|  
|SByte|Contient une valeur d'entier 8 bits signé.|Precision, Nullable, Default|  
|Chaîne|Contient des données caractères.|Unicode, FixedLength, MaxLength, Collation, Precision, Nullable, Default|  
|réflexion|Contient une heure.|Precision, Nullable, Default|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
