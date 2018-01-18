---
title: "fonction définie par modèle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1c9d438840a0b9c15597177ca4e6d870d526756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="model-defined-function"></a>fonction définie par modèle
A *fonction définie par modèle* est une fonction qui est définie dans un modèle conceptuel. Le corps d’une fonction définie par modèle est exprimé en [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), ce qui permet de la fonction d’exprimer indépendamment de règles ou langues prises en charge dans la source de données.  
  
 Une définition pour une fonction définie par modèle contient les informations suivantes :  
  
-   Nom de la fonction. (Requis)  
  
-   Type de la valeur de retour. (facultatif)  
  
    > [!NOTE]
    >  Si aucun type de retour n'est spécifié, la valeur de retour est void.  
  
-   Informations sur les paramètres. (facultatif)  
  
-   Un [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression qui définit le corps de la fonction.  
  
 Notez que les fonctions définies par modèle ne prennent pas en charge les paramètres de sortie. Cette restriction est en place de manière à ce que des fonctions définies par modèle puissent être composées.  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.  
  
 ![Modèle avec Date publiée](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit une fonction dans le modèle conceptuel qui retourne le nombre d'années écoulées depuis la publication d'une instance de `Book` (dans le diagramme ci-dessus).  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [Entity Data Model : types de données primitifs](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
