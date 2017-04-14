---
title: "Entity Data Model&#160;: types de donn&#233;es primitifs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Entity Data Model&#160;: types de donn&#233;es primitifs
Le modèle EDM \(Entity Data Model\) prend en charge un jeu de types de données primitifs abstraits \(comme String, Boolean, Int32, etc.\) qui permettent de définir des [propriétés](../../../../docs/framework/data/adonet/property.md) dans un modèle conceptuel.  Ces types de données primitifs sont des proxys pour les types de données primitifs réels qui sont pris en charge dans l'environnement de stockage ou d'hébergement, comme une base de données SQL Server ou le Common Language Runtime \(CLR\).  Le modèle EDM ne définit pas la sémantique des opérations ou des conversions sur les types de données primitifs ; cette sémantique est définie par l'environnement de stockage ou d'hébergement.  En général, les types de données primitifs dans le modèle EDM sont mappés aux types de données primitifs correspondants dans l'environnement de stockage ou d'hébergement.  Pour plus d'informations sur la façon dont Entity Framework mappe les types primitifs dans le modèle EDM aux types de données SQL Server, consultez [SqlClient pour les types Entity Framework](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  Le modèle EDM ne prend pas en charge les collections de types de données primitifs.  
  
 Pour plus d'informations sur les types de données structurées dans le modèle EDM, consultez [type d'entité](../../../../docs/framework/data/adonet/entity-type.md) et [type complexe](../../../../docs/framework/data/adonet/complex-type.md).  
  
## Types de données primitifs pris en charge dans le modèle EDM  
 Le tableau suivant répertorie les types de données primitifs pris en charge par le modèle EDM.  Le tableau répertorie également les [facettes](../../../../docs/framework/data/adonet/facet.md) qui peuvent être appliquées à chaque type de données primitif.  
  
|Type de données primitif|Description|Facettes applicables|  
|------------------------------|-----------------|--------------------------|  
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
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)