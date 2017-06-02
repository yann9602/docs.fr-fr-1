---
title: "fonction d&#233;clar&#233;e par mod&#232;le | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# fonction d&#233;clar&#233;e par mod&#232;le
Une *fonction déclarée par modèle* est une fonction déclarée dans un modèle conceptuel, mais qui n'est pas définie dans ce modèle conceptuel.  La fonction peut être définie dans l'environnement d'hébergement ou de stockage.  Par exemple, une fonction déclarée par modèle peut être mappée à une fonction définie dans une base de données, exposant ainsi les fonctionnalités côté serveur dans le modèle conceptuel.  
  
 La déclaration d'une fonction déclarée par modèle contient les informations suivantes :  
  
-   Nom de la fonction.  \(Requis\)  
  
-   Type de la valeur de retour.  \(facultatif\)  
  
    > [!NOTE]
    >  Si aucune valeur de retour n'est spécifiée, le type de retour est void.  
  
-   Informations sur les paramètres, notamment le nom et le type des paramètres.  \(facultatif\)  
  
## Exemple  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  En CSDL, une implémentation d'une fonction déclarée par modèle est une [importation de fonction](http://msdn.microsoft.com/fr-fr/125704ae-56c7-4233-80b7-389a10f3a65d).  Le CSDL suivant définit un conteneur d'entités avec une définition d'importation de fonction.  Notez que le type de retour pour la fonction est void, car aucun type de retour n'est spécifié.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)