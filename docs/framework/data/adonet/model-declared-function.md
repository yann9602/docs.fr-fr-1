---
title: "fonction déclarée par modèle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e47c89524bf149d862ae872c0c5956b7debd818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="model-declared-function"></a>fonction déclarée par modèle
A *fonction déclarée par modèle* est une fonction qui est déclarée dans un modèle conceptuel, mais n’est pas définie dans ce modèle conceptuel. La fonction peut être définie dans l'environnement d'hébergement ou de stockage. Par exemple, une fonction déclarée par modèle peut être mappée à une fonction définie dans une base de données, exposant ainsi les fonctionnalités côté serveur dans le modèle conceptuel.  
  
 La déclaration d'une fonction déclarée par modèle contient les informations suivantes :  
  
-   Nom de la fonction. (Requis)  
  
-   Type de la valeur de retour. (facultatif)  
  
    > [!NOTE]
    >  Si aucune valeur de retour n'est spécifiée, le type de retour est void.  
  
-   Informations sur les paramètres, notamment le nom et le type des paramètres. (facultatif)  
  
## <a name="example"></a>Exemple  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Dans le langage CSDL, une implémentation d’une fonction déclarée par modèle est un [importation de fonction](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d). Le CSDL suivant définit un conteneur d'entités avec une définition d'importation de fonction. Notez que le type de retour pour la fonction est void, car aucun type de retour n’est spécifié.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés du modèle de données Entity](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
