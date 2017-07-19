---
title: "Proc&#233;dure&#160;: d&#233;finir la cha&#238;ne de connexion | Microsoft Docs"
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
  - "ESQL"
  - "jsharp"
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: d&#233;finir la cha&#238;ne de connexion
Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel.  Cette rubrique se base sur le modèle conceptuel de vente [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832).  Le modèle de vente AdventureWorks Sales Model est utilisé dans toutes les rubriques liées aux tâches de la documentation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Cette rubrique suppose que vous avez déjà configuré [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et défini le modèle de vente AdventureWorks Sales Model.  Pour plus d'informations, consultez [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/fr-fr/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  Les procédures de cette rubrique figurent également dans [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/fr-fr/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Si vous utilisez l'Assistant [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] dans un projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)], il génère automatiquement un fichier .edmx et configure le projet pour qu'il utilise [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### Pour définir la chaîne de connexion Entity Framework  
  
-   Ouvrez le fichier de configuration de l'application \(app.config\) du projet et ajoutez la chaîne de connexion suivante :  
  
  
  
     Si votre projet ne comprend pas de fichier de configuration de l'application, vous pouvez en ajouter un. Pour cela, sélectionnez **Ajouter un nouvel élément** dans le menu **Projet**, sélectionnez la catégorie **Général**, puis **Fichier de configuration de l'application** et cliquez sur **Ajouter**.  
  
## Voir aussi  
 [Quickstart](http://msdn.microsoft.com/fr-fr/0bc534be-789f-4819-b9f6-76e51d961675)   
 [How to: Create a New .edmx File](http://msdn.microsoft.com/fr-fr/beb8189e-e51c-4051-839c-9902c224abf2)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/fr-fr/91076853-0881-421b-837a-f582f36be527)