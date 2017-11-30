---
title: "Fonctions définies par l'utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff13a123bcb2c61d786f2156e600a16cdd6bb31e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions"></a>Fonctions définies par l'utilisateur
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des méthodes dans votre modèle objet pour représenter des fonctions définies par l'utilisateur. Vous désignez des méthodes comme des fonctions en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>. Pour plus d’informations, consultez [le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Pour éviter une exception <xref:System.InvalidOperationException>, les fonctions définies par l'utilisateur dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doivent prendre l'une des formes suivantes :  
  
-   Fonction encapsulée comme un appel de méthode disposant des attributs de mappage appropriés. Pour plus d’informations, consultez [mappage basé sur l’attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Méthode SQL statique spécifique à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Fonction prise en charge par une méthode [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code. Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] utilisent généralement [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour mapper des fonctions définies par l'utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : utiliser des fonctions définies par l’utilisateur scalaires](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Décrit comment implémenter une fonction qui retourne des valeurs scalaires.  
  
 [Comment : utiliser des fonctions définies par l’utilisateur de table](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Décrit comment implémenter une fonction qui retourne des valeurs de table.  
  
 [Comment : appeler des fonctions définies par l’utilisateur Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Décrit comment passer des appels inline à des fonctions et les différences d'exécution lorsque l'appel est rendu inline.
