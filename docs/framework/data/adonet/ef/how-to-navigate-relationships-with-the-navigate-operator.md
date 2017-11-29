---
title: "Comment : naviguer parmi les relations avec l'opérateur Navigate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38b2a6630d967519f3c907c60944d943c6b9b720
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a>Comment : naviguer parmi les relations avec l'opérateur Navigate
Cette rubrique montre comment exécuter une commande par rapport à un modèle conceptuel en utilisant un objet <xref:System.Data.EntityClient.EntityCommand> et comment récupérer les résultats de <xref:System.Data.Metadata.Edm.RefType> en utilisant un objet <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1.  Ajouter le [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) à votre projet et configurer votre projet pour utiliser le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment parcourir les relations dans [!INCLUDE[esql](../../../../../includes/esql-md.md)] à l’aide de la [naviguer](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) opérateur. Le `Navigate` opérateur accepte les paramètres suivants : une instance d’une entité, le type de relation, la fin de la relation et le début de la relation. Si vous le souhaitez, vous pouvez passer uniquement une instance d’une entité et le type de relation pour le `Navigate` opérateur.  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [Langage Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
