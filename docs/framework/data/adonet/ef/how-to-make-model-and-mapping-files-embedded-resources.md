---
title: "Proc&#233;dure&#160;: faire des fichiers de mod&#232;le et de mappage des ressources incorpor&#233;es | Microsoft Docs"
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
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: faire des fichiers de mod&#232;le et de mappage des ressources incorpor&#233;es
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permet de déployer des fichiers de mappage et de modèle en tant que ressources incorporées d'une application.  L'assembly comprenant les fichiers de mappage et de modèle incorporés doit être chargé dans le même domaine d'application que la connexion d'entité.  Pour plus d'informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  Par défaut, les outils [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] incorporent les fichiers de mappage et de modèle. Lorsque vous définissez manuellement les fichiers de mappage et de modèle, utilisez cette procédure pour garantir que les fichiers sont déployés en tant que ressources incorporées avec une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Pour conserver des ressources incorporées, vous devez répéter cette procédure chaque fois que les fichiers de mappage et de modèle sont modifiés.  
  
### Pour incorporer les fichiers de mappage et de modèle  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez le fichier conceptuel \(.csdl\).  
  
2.  Dans le volet **Propriétés**, affectez la valeur **Ressource incorporée** à **Action de génération**.  
  
3.  Répétez les étapes 1 et 2 pour le fichier de stockage \(.ssdl\) et le fichier de mappage \(.msl\).  
  
4.  Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier App.config, puis modifiez le paramètre `Metadata` dans l'attribut `connectionString` en appliquant l'un des formats suivants :  
  
    -   `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=` `res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Pour plus d'informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## Exemple  
 La chaîne de connexion suivante référence les fichiers de mappage et de modèle incorporés pour le modèle de vente [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832).  Cette chaîne de connexion est stockée dans le fichier App.config du projet.  
  
  
  
## Voir aussi  
 [Modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)   
 [Procédure : définir la chaîne de connexion](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)   
 [Procédure : générer une chaîne de connexion pour EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/fr-fr/91076853-0881-421b-837a-f582f36be527)